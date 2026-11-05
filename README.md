<html lang="id">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Anggota - Kas Pemuda Neglasari</title>
<style>
:root{--green:#176b45;--green2:#e9f5ee;--ink:#17251e;--muted:#6c7b72;--line:#e4ebe6;--bg:#f5f8f6;--white:#fff;--red:#b54747}
*{box-sizing:border-box}body{margin:0;background:var(--bg);font:15px/1.5 system-ui,-apple-system,Segoe UI,Roboto,sans-serif;color:var(--ink)}
header{background:linear-gradient(120deg,#145b3b,#238457);color:white;padding:25px 18px 32px}
.wrap{max-width:1000px;margin:auto;padding:0 16px}.brand{font-size:12px;letter-spacing:2px;opacity:.85;font-weight:700}.hero{display:flex;justify-content:space-between;align-items:center;gap:14px}.hero h1{font-size:27px;margin:8px 0 3px}.hero p{margin:0;opacity:.85}.pill{border:1px solid #ffffff70;border-radius:999px;padding:7px 12px;font-size:12px}
main{margin-top:-18px;padding-bottom:35px}.tabs{display:flex;gap:8px;flex-wrap:wrap;background:white;border:1px solid var(--line);border-radius:14px;padding:8px;box-shadow:0 5px 20px #173d2910}
button,select,input{font:inherit}button{border:0;border-radius:10px;padding:10px 14px;background:var(--green);color:white;font-weight:650;cursor:pointer}.tabs button{background:transparent;color:var(--muted)}.tabs button.active{background:var(--green2);color:var(--green)}
.grid{display:grid;grid-template-columns:repeat(3,1fr);gap:13px;margin:16px 0}.card{background:white;border:1px solid var(--line);border-radius:15px;padding:17px;box-shadow:0 3px 12px #173d2908}.stat small{color:var(--muted);display:block}.stat strong{font-size:24px;display:block;margin-top:5px}.section{display:flex;justify-content:space-between;align-items:center;margin:22px 0 10px;gap:12px}.section h2{font-size:18px;margin:0}.muted{color:var(--muted)}.row{display:flex;gap:10px;flex-wrap:wrap;align-items:center}.field{display:flex;flex-direction:column;gap:5px;flex:1;min-width:150px}.field label{font-size:12px;color:var(--muted);font-weight:650}.field input,.field select{width:100%;border:1px solid var(--line);border-radius:9px;padding:10px;background:white;color:var(--ink)}.form{display:grid;grid-template-columns:repeat(2,1fr);gap:12px}.form button{align-self:end}.tablewrap{overflow:auto}table{width:100%;border-collapse:collapse;min-width:560px}th,td{text-align:left;padding:12px 9px;border-bottom:1px solid var(--line);font-size:13px}th{color:var(--muted);font-weight:650}.status{display:inline-block;padding:4px 8px;border-radius:999px;background:var(--green2);color:var(--green);font-size:11px;font-weight:700}.pending{background:#fff4df;color:#96651b}.hidden{display:none}.notice{background:#fff8e9;border:1px solid #f1dfb7;color:#76531a;border-radius:12px;padding:12px 14px;font-size:13px;margin-top:14px}.empty{padding:18px;color:var(--muted);text-align:center}.danger{background:#fff0f0;color:var(--red)}footer{text-align:center;color:var(--muted);font-size:12px;padding:25px}
@media(max-width:650px){.grid{grid-template-columns:1fr}.hero h1{font-size:23px}.form{grid-template-columns:1fr}.section{align-items:flex-start;flex-direction:column}}
</style>
</head>
<body>
<header><div class="wrap hero"><div><div class="brand">SISTEM KAS WARGA</div><h1>Pemuda Neglasari</h1><p>Catatan kas yang transparan dan mudah diakses.</p></div><span class="pill">Kas Pemuda</span></div></header>
<main class="wrap">
<nav class="tabs" aria-label="Navigasi"><button class="active" data-tab="anggota">Dashboard Anggota</button></nav>
<section id="anggota">
<div class="grid">
<div class="card stat"><small>Total saldo kas</small><strong id="saldoAnggota">Rp0</strong></div>
<div class="card stat"><small>Anggota terdaftar</small><strong id="jumlahAnggota">0</strong></div>
<div class="card stat"><small>Pembayaran tercatat</small><strong id="jumlahBayar">0</strong></div>
</div>
<div class="section"><h2>Status pembayaran anggota</h2><span class="muted">Data contoh lokal</span></div>
<div class="card"><div class="tablewrap"><table><thead><tr><th>Nama anggota</th><th>Bulan</th><th>Nominal</th><th>Status</th></tr></thead><tbody id="tabelAnggota"></tbody></table></div></div>
<div class="section"><h2>Form pembayaran kas</h2></div>
<div class="card">
<form id="formBayar" class="form">
<div class="field"><label>Nama anggota</label><input id="namaBayar" required placeholder="Nama lengkap"></div>
<div class="field"><label>Bulan pembayaran</label><select id="bulanBayar"><option>Januari</option><option>Februari</option><option>Maret</option><option>April</option><option>Mei</option><option>Juni</option><option>Juli</option><option>Agustus</option><option>September</option><option>Oktober</option><option>November</option><option>Desember</option></select></div>
<div class="field"><label>Nominal (Rp)</label><input id="nominalBayar" type="number" min="1" required placeholder="Contoh: 10000"></div>
<div class="field"><label>Metode pembayaran</label><select id="metodeBayar"><option>Tunai</option><option>Transfer / QRIS</option></select></div>
<div class="field"><label>Bukti transfer (opsional untuk demo)</label><input id="buktiBayar" type="file" accept="image/*"></div>
<button type="submit">Kirim pembayaran</button>
</form>
<div class="notice">Ini masih prototipe: pengiriman pembayaran hanya tersimpan di browser perangkat ini. Transfer/QRIS belum terhubung ke rekening dan bukti belum dikirim ke bendahara.</div>
</div>
</section>

</main>
<footer>Pemuda Neglasari · Prototipe website kas</footer>
<script>
const key='neglasariKasDemoV1';
let data=JSON.parse(localStorage.getItem(key)||'{"anggota":[],"bayar":[],"transaksi":[]}');
const rupiah=n=>'Rp'+Number(n||0).toLocaleString('id-ID');
const save=()=>{localStorage.setItem(key,JSON.stringify(data));render()};
const total=(jenis)=>data.transaksi.filter(x=>x.jenis===jenis).reduce((a,x)=>a+x.nominal,0);
const totalBayar=()=>data.bayar.filter(x=>x.status==='Dikonfirmasi').reduce((a,x)=>a+x.nominal,0);
const saldo=()=>totalBayar()+total('masuk')-total('keluar');
function render(){
 document.getElementById('saldoAnggota').textContent=rupiah(saldo());
 document.getElementById('saldoBendahara').textContent=rupiah(saldo());
 document.getElementById('pemasukan').textContent=rupiah(totalBayar()+total('masuk'));
 document.getElementById('pengeluaran').textContent=rupiah(total('keluar'));
 document.getElementById('jumlahAnggota').textContent=data.anggota.length;
 document.getElementById('jumlahBayar').textContent=data.bayar.filter(x=>x.status==='Dikonfirmasi').length;
 document.getElementById('tabelAnggota').innerHTML=data.bayar.length?data.bayar.map(x=>`<tr><td>${esc(x.nama)}</td><td>${esc(x.bulan)}</td><td>${rupiah(x.nominal)}</td><td><span class="status ${x.status==='Menunggu'?'pending':''}">${x.status}</span></td></tr>`).join(''):'<tr><td colspan="4" class="empty">Belum ada pembayaran.</td></tr>';
 document.getElementById('tabelKonfirmasi').innerHTML=data.bayar.length?data.bayar.map((x,i)=>`<tr><td>${esc(x.nama)}</td><td>${esc(x.bulan)}</td><td>${rupiah(x.nominal)}</td><td>${esc(x.metode)}</td><td>${x.status}</td><td>${x.status==='Menunggu'?`<button onclick="konfirmasi(${i})">Konfirmasi</button>`:'—'}</td></tr>`).join(''):'<tr><td colspan="6" class="empty">Belum ada pembayaran masuk.</td></tr>';
 document.getElementById('tabelTransaksi').innerHTML=data.transaksi.length?data.transaksi.map(x=>`<tr><td>${x.tanggal}</td><td>${esc(x.ket)}</td><td>${x.jenis==='masuk'?'Pemasukan':'Pengeluaran'}</td><td>${rupiah(x.nominal)}</td></tr>`).join(''):'<tr><td colspan="4" class="empty">Belum ada transaksi.</td></tr>';
}
function esc(s){return String(s).replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]))}
window.konfirmasi=i=>{data.bayar[i].status='Dikonfirmasi';save()};
document.querySelectorAll('[data-tab]').forEach(b=>b.addEventListener('click',()=>{document.querySelectorAll('[data-tab]').forEach(x=>x.classList.toggle('active',x===b));document.getElementById('anggota').classList.toggle('hidden',b.dataset.tab!=='anggota');document.getElementById('bendahara').classList.toggle('hidden',b.dataset.tab!=='bendahara')}));
document.getElementById('formAnggota').addEventListener('submit',e=>{e.preventDefault();data.anggota.push(document.getElementById('namaAnggota').value.trim());e.target.reset();save()});
document.getElementById('formBayar').addEventListener('submit',e=>{e.preventDefault();const f=document.getElementById('buktiBayar');data.bayar.push({nama:document.getElementById('namaBayar').value.trim(),bulan:document.getElementById('bulanBayar').value,nominal:Number(document.getElementById('nominalBayar').value),metode:document.getElementById('metodeBayar').value,status:'Menunggu'});e.target.reset();save();alert('Pembayaran demo tercatat sebagai Menunggu. Bendahara dapat mengonfirmasi pada tab bendahara.')});
document.getElementById('formTransaksi').addEventListener('submit',e=>{e.preventDefault();data.transaksi.push({jenis:document.getElementById('jenis').value,ket:document.getElementById('ket').value.trim(),nominal:Number(document.getElementById('nominal').value),tanggal:new Date().toLocaleDateString('id-ID')});e.target.reset();save()});
document.getElementById('reset').addEventListener('click',()=>{if(confirm('Hapus seluruh data demo di browser ini?')){data={anggota:[],bayar:[],transaksi:[]};save()}});
render();
</script>
</body></html>

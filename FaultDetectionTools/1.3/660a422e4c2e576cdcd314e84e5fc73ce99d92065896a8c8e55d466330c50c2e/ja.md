```
 γ = fdimmperf(sysr::FDFilterIF, sysref::Union{FDFilterIF,FDIModel}[, nrmflag])
```

故障検出フィルタ内部形式オブジェクト `sysr::FDFilterIF` のモデルマッチング性能 `γ` を、故障検出参照フィルタ内部形式 `sysref::FDFilterIF` に対して計算します。`R(λ)` が故障検出フィルタ内部形式 `sysr.sys` の伝達関数行列であり、`Mr(λ)` が故障検出参照フィルタ内部形式 `sysref.sys` の伝達関数行列である場合、`γ` は `R(λ)-Mr(λ)` の H∞-ノルムです（`nrmflag = Inf` の場合、デフォルト）または `R(λ)-Mr(λ)` の H2-ノルムです（`nrmflag = 2` の場合）。`γ` の値は、`R(λ)-Mr(λ)` の不安定な差分の場合、または `nrmflag = 2` で連続時間システムの伝達関数行列 `R(λ)-Mr(λ)` が厳密に適切でない場合には無限大になります。一般に、`R(λ)` と `Mr(λ)` は、制御入力、外乱入力、故障入力、ノイズ入力、補助入力の入力の分割に従って、`R(λ) = [ Ru(λ) Rd(λ) Rf(λ) Rw(λ) Ra(λ) ]` および `Mr(λ) = [ Mru(λ) Mrd(λ) Mrf(λ) Mrw(λ) Mra(λ) ]` のように分割されます。`R(λ)` の非ゼロ成分に対応する `Mr(λ)` の無効成分はゼロであると仮定されます。

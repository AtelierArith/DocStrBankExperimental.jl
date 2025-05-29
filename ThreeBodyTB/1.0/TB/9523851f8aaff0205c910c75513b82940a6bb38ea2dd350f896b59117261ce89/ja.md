```
mutable struct tb{T}
```

実空間におけるキー tight-binding 情報を保持します。Wannier90 の `_hr.dat` ファイルのようなものです。また、`tb_crys` オブジェクトの一部です。密行列バージョンで、`tb_sparse` も参照してください。

# 保持するもの

  * `H::Array{Complex{T},4}` ハミルトニアン。`nwan`×`nwan`×`nr`×`nspin`
  * `ind_array::Array{Int64,3}` `nr`×3、TB オブジェクトの r 空間スーパセルを保持します。
  * `r_dict::Dict` キーは [0,0,0] のような三つの Int で、対応する `ind_array` インデックスを返します。
  * `nwan::Int` 軌道の数（一般化されたワニエ関数）。
  * `nspin::Int` スピンの数（2=磁気）
  * `nr::Int64` R 空間スーパセルの数。
  * `nonorth::Bool` : 非直交の場合は `true`。このコードではほぼ常に `true` です。
  * `S::Array{Complex{T},3}` : 重なり行列、`H` のように整理されています。
  * `scf::Bool` 自己無矛盾が必要な場合は `true` に等しい（通常、フィット `tb` では `true`、DFT から直接の場合は `false`）。
  * `h1::Array{T,3}` すでに計算されている場合、scf 計算によって決定された項を持っています。

```
qmpo,qmps = MPO(Qlabels,mpo,mps[,newnorm=true,setflux=false,flux=...,randomize=true,override=true,lastfluxzero=false])
```

入力 `mpo` と `Qlabels` から量子数 MPO `qmpo` を作成します。`Qlabels` は `Qnum` のベクトルです。また、入力の密な `mps` から量子数 MPS `qmps` も返します。

# オプション引数

  * `mps::MPS`: 密な MPS
  * `Qlabels::Array{Array{Qnum,1},1}`: 各物理インデックスの量子数ラベル（このベクトルのサイズで物理インデックスラベルを割り当てます）
  * `newnorm::Bool`: MPS テンソルの新しいノルムを設定
  * `setflux::Bool`: MPS テンソルの総フラックスを強制するためのトグル
  * `flux::Qnum`: `setflux=true` の場合に総 MPS フラックスを強制する量子数
  * `randomize::Bool`: フラックスがゼロテンソルを強制する場合、最後のテンソルをランダム化
  * `lastfluxzero::Bool`: 最右のフラックスがゼロであるべきかどうかを決定

参照: [`Qnum`](@ref)

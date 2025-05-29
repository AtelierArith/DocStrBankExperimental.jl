```
qmps = MPS(Qlabels,arr[,oc=1,newnorm=true,setflux=false,flux=...,randomize=true,override=true,lastfluxzero=false])
```

配列 `arr` を量子数 MPS `qmps` に変換し、量子数は `Qlabels` の量子数ベクトルの配列から割り当てられます。

# オプション引数

  * `mps::MPS`: 密な MPS
  * `Qlabels::Array{Array{Qnum,1},1}`: 各物理インデックスの量子数ラベル（このベクトルのサイズで物理インデックスラベルを割り当てます）
  * `oc::Integer`: 整数
  * `newnorm::Bool`: MPS テンソルの新しいノルムを設定
  * `setflux::Bool`: これを MPS テンソルの総フラックスに強制するためのトグル
  * `flux::Qnum`: setflux=true の場合に総 MPS フラックスに強制する量子数
  * `randomize::Bool`: フラックスがゼロテンソルを強制する場合、最後のテンソルをランダム化
  * `lastfluxzero::Bool`: 最右のフラックスがゼロであるべきかどうかを決定

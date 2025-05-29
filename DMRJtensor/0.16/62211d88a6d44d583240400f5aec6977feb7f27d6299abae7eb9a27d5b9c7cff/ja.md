```
makeqMPS(Qlabels,mps[,newnorm=true,setflux=false,flux=...,randomize=true,override=true,lastfluxzero=false])
```

は、`Qlabels` に従って通常の MPS から量子数 MPS を作成します。

# オプション引数

  * `mps::MPS`: 密な MPS
  * `Qlabels::Array{Array{Qnum,1},1}`: 各物理インデックスの量子数ラベル（このベクトルのサイズで物理インデックスラベルを割り当てます）
  * `newnorm::Bool`: MPS テンソルの新しいノルムを設定
  * `setflux::Bool`: これを MPS テンソルの総フラックスに強制するためのトグル
  * `flux::Qnum`: setflux=true の場合に総 MPS フラックスに強制する量子数
  * `randomize::Bool`: フラックスがゼロテンソルを強制する場合に最後のテンソルをランダム化
  * `lastfluxzero::Bool`: 最右のフラックスがゼロであるべきかどうかを決定

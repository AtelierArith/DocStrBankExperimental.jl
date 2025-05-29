```
MPS(Qlabels,mps[,newnorm=true,setflux=false,flux=...,randomize=true,override=true,lastfluxzero=false])
```

MPS `mps` を量子数バージョンに変換し、`Qlabels` をすべてのサイトに均等に割り当てます。

# オプション引数

  * `mps::MPS`: 密な MPS
  * `Qlabels::Array{Array{Qnum,1},1}`: 各物理インデックスの量子数ラベル（このベクトルのサイズで物理インデックスラベルを割り当てます）
  * `newnorm::Bool`: MPS テンソルの新しいノルムを設定
  * `setflux::Bool`: MPS テンソルの総フラックスを強制するためのトグル
  * `flux::Qnum`: `setflux=true` の場合に総 MPS フラックスを強制する量子数
  * `randomize::Bool`: フラックスがゼロテンソルを強制する場合に最後のテンソルをランダム化
  * `lastfluxzero::Bool`: 最右のフラックスがゼロであるべきかどうかを決定

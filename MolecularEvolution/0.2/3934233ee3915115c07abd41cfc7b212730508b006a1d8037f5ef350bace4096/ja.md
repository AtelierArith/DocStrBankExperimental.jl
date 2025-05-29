```
SWM_prob_grid(part::SWMPartition{PType}) where {PType <: MultiSitePartition}
```

各モデルごとの各サイトの確率の行列（確率ドメインで - ログではない！）とログ確率オフセットを返します。

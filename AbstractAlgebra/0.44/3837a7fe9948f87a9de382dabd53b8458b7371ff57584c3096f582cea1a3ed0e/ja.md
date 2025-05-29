```
map_coefficients(f, p::SeriesElem{<: RingElement}; cached::Bool=true, parent::PolyRing)
```

系列 `p` の各非ゼロ係数に `f` を適用することで変換します。

オプションの `parent` キーワードが提供されている場合、ポリノミアルは `parent` の要素になります。親オブジェクトのキャッシングは `cached` キーワード引数を介して制御できます。

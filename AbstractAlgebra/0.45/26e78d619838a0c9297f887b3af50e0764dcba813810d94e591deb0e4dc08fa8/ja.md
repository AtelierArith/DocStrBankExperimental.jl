```
change_base_ring(R::Ring, p::SeriesElem{<: RingElement}; parent::PolyRing)
```

非ゼロ係数の `p` を `R` に強制的に変換して得られる系列を返します。

オプションの `parent` キーワードが提供されると、系列は `parent` の要素になります。親オブジェクトのキャッシングは、`cached` キーワード引数を介して制御できます。

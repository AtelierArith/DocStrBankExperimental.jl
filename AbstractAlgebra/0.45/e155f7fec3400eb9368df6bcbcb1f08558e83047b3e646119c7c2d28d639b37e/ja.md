```
change_base_ring(R::Ring, p::PolyRingElem{<: RingElement}; parent::PolyRing)
```

非ゼロ係数の `p` を `R` に強制的に変換して得られる多項式を返します。

オプションの `parent` キーワードが提供されている場合、多項式は `parent` の要素になります。親オブジェクトのキャッシュは、`cached` キーワード引数を介して制御できます。

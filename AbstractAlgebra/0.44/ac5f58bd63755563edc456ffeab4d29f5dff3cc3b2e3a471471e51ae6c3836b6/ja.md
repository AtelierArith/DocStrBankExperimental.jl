```
map_coefficients(f, p::PolyRingElem{<: RingElement}; cached::Bool=true, parent::PolyRing)
```

多項式 `p` の各非ゼロ係数に `f` を適用することで変換します。

オプションの `parent` キーワードが提供されている場合、多項式は `parent` の要素になります。親オブジェクトのキャッシングは、`cached` キーワード引数を介して制御できます。

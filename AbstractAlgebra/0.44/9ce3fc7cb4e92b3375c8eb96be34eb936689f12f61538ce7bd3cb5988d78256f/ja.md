```
map_coefficients(f, p::MPolyRingElem{<: RingElement}; parent::MPolyRing)
```

多項式 `p` の各非ゼロ係数に `f` を適用することで変換します。

オプションの `parent` キーワードが提供される場合、多項式は `parent` の要素になります。親オブジェクトのキャッシュは、`cached` キーワード引数を介して制御できます。

```
hermitian_lattice(E::NumField, basis::MatElem; gram = nothing,
			                    check::Bool = true) -> HermLat
```

行列 `basis` と次数 2 の数体 `E` が与えられたとき、`basis` の行によって張られるエルミート格子を、グラム行列 `gram` を用いて `E` 上のエルミート空間内で返します。

`gram` が指定されていない場合、周囲の空間のグラム行列は、`basis` の列数のサイズを持つ `E` 上の単位行列になります。

デフォルトでは、`basis` がフルランクであることが確認されます。このテストは、`check` を false に設定することで無効にできます。

```
hermitian_lattice(E::NumField, basis::MatElem; gram = nothing,
			                    check::Bool = true) -> HermLat
```

行列 `basis` と次数 2 の数体 `E` が与えられたとき、グラム行列 `gram` を持つ `E` 上のエルミート空間内で `basis` の行によって張られるエルミート格子を返します。

`gram` が指定されていない場合、周囲空間のグラム行列は `basis` の列数のサイズの `E` 上の単位行列になります。

デフォルトでは、`basis` がフルランクであることがチェックされます。このテストは、`check` を false に設定することで無効にできます。

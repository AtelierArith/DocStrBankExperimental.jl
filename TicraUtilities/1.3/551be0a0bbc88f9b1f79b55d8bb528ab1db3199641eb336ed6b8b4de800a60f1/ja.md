```
TEPscatter <: TEP
```

TICRA互換の表形式電気特性（TEP）ファイルからの散乱面の単一周波数のデータを含む構造体（すなわち、GRASP8以降使用されているTEPファイルの旧スタイルの元の定義）。

## フィールド

  * `title::String`: タイトル文字列を含む。
  * `theta`: 度単位のθ値を含む`AbstractRange`。
  * `phi`: 度単位のϕ値を含む`AbstractRange`。
  * `sff::Array{ComplexF64, 4}`: 前面入射の反射係数を含む。
  * `sfr::Array{ComplexF64, 4}`: 背面入射の透過係数を含む。
  * `srf::Array{ComplexF64, 4}`: 前面入射の透過係数を含む。
  * `srr::Array{ComplexF64, 4}`: 背面入射の反射係数を含む。

`s`がフィールド`sff`、`sfr`、`srf`、および`srr`のいずれかを表す場合、`size(s) = (2, 2, length(theta), length(phi))`であり、2×2行列`s[:,:,i,j]`は`[sθθ sθϕ; sϕθ sϕϕ]`の順序で配置される。

## 参照

  * `TEPperiodic`

```
parsemiss(Q, x::Vector{Union{String, Missing}})
```

欠損データを許可する文字列ベクトルの解析。

  * `Q` : 型 `String` の解析から得られる型。
  * `x` : `missing`（型 `Missing`）の観測値を含む文字列ベクトル。

例を参照してください。

## 例

```julia
using Jchemo

x = ["1"; "3.2"; missing]
x_p = parsemiss(Float64, x)
```

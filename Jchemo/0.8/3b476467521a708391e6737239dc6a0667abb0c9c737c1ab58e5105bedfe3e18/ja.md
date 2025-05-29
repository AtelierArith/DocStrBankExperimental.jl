```
convertdf(df::DataFrame; miss = nothing, typ)
```

データフレームの列を指定された型に変換します。

  * `df` : データフレーム。
  * `miss` : `df` 内で `missing`（型 `Missing`）として宣言されるデータを識別するために使用されるコード。関数 `recod_miss` を参照してください。
  * `typ` : 新しいデータフレームの列のターゲット型のベクトル。

## 例

```julia
using Jchemo, DataFrames
```

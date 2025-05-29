```
RimuIO.save_df(filename, df::DataFrame; kwargs...)
```

データフレームをArrow形式で保存します。

キーワード引数は[`Arrow.write`](https://arrow.apache.org/julia/dev/reference/#Arrow.write)に渡されます。大きな`DataFrame`（10,000行以上）については、デフォルトで圧縮が有効になっています。

`DataFrame`のテーブルレベルのメタデータは、キーワード引数`metadata`で上書きされない限り、Arrowメタデータ（`String`値）として保存されます。

また、[`RimuIO.load_df`](@ref)も参照してください。

```
print([io::IO = stdout,] data::Vector, lidict::LineInfoDict; kwargs...)
```

`io`にプロファイリング結果を出力します。このバリアントは、以前の[`retrieve`](@ref)呼び出しによってエクスポートされた結果を調べるために使用されます。バックトレースのベクター`data`と行情報の辞書`lidict`を提供します。

有効なキーワード引数の説明については、`Profile.print([io], data)`を参照してください。

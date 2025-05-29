```
pooled!(df, cols::Type=Union{AbstractString,Missing})
```

`DataFrames.categorical!`のように、列を`PooledArray`に変換します。

!!! warning
    このメソッドは最初の引数に対して型特異的ではなく、`DataFrames.jl`への依存関係を排除するためです。それでも、最初の引数には`DataFrame`を期待します。


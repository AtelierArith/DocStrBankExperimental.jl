```
all_variable_symbols(indp)
```

システム内の変数シンボルのベクトルを返し、観測された量を含みます。

このインターフェースを使用してシンボリックインデックスで `Base.getindex` を実装するタイプの場合、`sys[allvariables]` は `valp[all_variable_symbols(indp)]` の省略形として使用できます。

参照: [`allvariables`](@ref).

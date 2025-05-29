```
istunable(x, default = true)
```

シンボリック変数 `x` が自動調整アルゴリズムのために調整可能としてマークされているかどうかを判断します。

`default` は、`tunable` メタデータがない変数を調整可能と見なすかどうかを示します。

調整可能なパラメータを作成するには

```
@parameters u [tunable=true]
```

も参照してください [`tunable_parameters`](@ref), [`getbounds`](@ref)

```
NLLSsolver.getvars(mycost, vars)
```

`mycost`が依存する変数を返します。返り値は変数のタプルでなければなりません。

良好なパフォーマンスのためには、出力変数が具体的な型を持つことが重要です。例えば、`Any`ではありません。

# 例

最初と3番目の変数に依存する問題`MyCost <: AbstractCost`の場合、

```julia
    NLLSsolver.getvars(::MyCost, vars) = (vars[1], vars[3])
```

!!! tip
    `vars`が型の異種混合である場合、特定の変数に型アノテーションを追加してください。例えば、


`(vars[1]::Matrix{T}, vars[3]::Vector{T})`は`MyCost{T}`の場合です。

!!! note
    必要なユーザー専門のAPI関数です。


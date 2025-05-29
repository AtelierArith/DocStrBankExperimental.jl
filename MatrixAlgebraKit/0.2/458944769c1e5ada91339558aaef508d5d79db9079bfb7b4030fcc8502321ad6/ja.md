```
MatrixAlgebraKit.default_algorithm(f, A; kwargs...)
```

与えられた因子分解関数 `f` と入力 `A` に対してデフォルトのアルゴリズムを選択します。一般的に、明示的にアルゴリズムが指定されていない場合は、[`select_algorithm`](@ref) によって呼び出されます。

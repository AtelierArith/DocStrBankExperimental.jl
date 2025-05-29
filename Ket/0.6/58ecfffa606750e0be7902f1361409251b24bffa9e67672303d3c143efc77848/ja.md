```
entanglement_robustness(
    ρ::AbstractMatrix{T},
    dims::AbstractVecOrTuple = _equal_sizes(ρ),
    n::Integer = 1;
    noise::String = "white"
    ppt::Bool = true,
    inner::Bool = false,
    verbose::Bool = false,
    dualize::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

状態 `ρ` のエンタングルメントロバストネスを、サブシステムの次元 `dims` を用いて、DPS階層のレベル `n` で下限（または上限）します（`inner = true` の場合は内側DPS）。引数 `noise` は使用するノイズの種類を示します："white"（デフォルト）、"separable"、または "general"。引数 `ppt` は部分転置制約を含めるかどうかを示します。引数 `dualize` は双対問題が代わりに解かれるかどうかを決定します。警告：これはパフォーマンスにとって重要であり、正しい選択はソルバーに依存します。

ロバストネスと証人 W を返します（`inner = true` の場合、これは有効なエンタングルメント証人でない可能性があることに注意してください）。

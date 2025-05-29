```
Duplicated(x, ∂f_∂x)
```

[`autodiff`](@ref Enzyme.autodiff) の関数引数 `x` を重複としてマークすると、Enzyme はそのような引数に関して自動微分を行い、`dx` が勾配の累積器として機能します（したがって、$\partial f / \partial x$ は `∂f_∂x` に *加算されます*）。

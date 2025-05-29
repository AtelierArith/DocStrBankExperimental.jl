```
infinite_domain(prefs::AbstractArray{<:DependentParameterRef})::InfiniteArrayDomain
```

無限の依存パラメータのコンテナ `prefs` に関連付けられた無限のドメインを返します。コンテナ `prefs` が不完全な場合はエラーが発生します。

**例**

```julia-repl
julia> infinite_domain(x)
ZeroMeanDiagNormal(
dim: 2
μ: [0.0, 0.0]
Σ: [1.0 0.0; 0.0 1.0]
)
```

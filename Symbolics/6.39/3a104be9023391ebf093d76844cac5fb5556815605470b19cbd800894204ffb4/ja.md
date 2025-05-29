```julia
≳(lhs, rhs) -> Any

```

二つの [`Num`](@ref) インスタンス、または `Num` と `Number` から [`Inequality`](@ref) を作成します。

# 例

```jldoctest
julia> using Symbolics

julia> @variables x y;

julia> x ≳ y
x ≳ y

julia> x - y ≳ 0
x - y ≳ 0
```

```
flatten(t::AbstractTensor) -> Tensor
flatten(a::AbstractLinear{<:AbstractTensor}) -> AbstractLinear{Tensor}
```

すべてのテンソルコンポーネントを再帰的に取得し、結果を連結します。この関数は線形です。

参照：[ `cat`](@ref)。

# 例

```jldoctest
julia> t = Tensor('x', Tensor('y', Tensor('z', 'w')))
'x'⊗('y'⊗('z'⊗'w'))

julia> flatten(t)
'x'⊗'y'⊗'z'⊗'w'
```

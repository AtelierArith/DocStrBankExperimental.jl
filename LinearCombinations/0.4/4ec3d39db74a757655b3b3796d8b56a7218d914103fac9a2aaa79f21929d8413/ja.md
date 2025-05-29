```
cat(t::AbstractTensor...) -> Tensor
```

引数として与えられたテンソルを連結します。この関数は多重線形です。

関連情報として[`flatten`](@ref)を参照してください。

# 例

```jldoctest
julia> LinearCombinations.cat(Tensor('x'), Tensor('y', Tensor('z', 'w')))
'x'⊗'y'⊗('z'⊗'w')
```

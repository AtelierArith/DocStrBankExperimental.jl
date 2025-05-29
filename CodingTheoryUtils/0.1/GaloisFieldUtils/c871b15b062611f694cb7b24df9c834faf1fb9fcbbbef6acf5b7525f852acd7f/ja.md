```
get_conjugates(β::F)::Array{F,1} where F <: GaloisFields.AbstractExtensionField
```

有限体の要素の共役を計算します。

# 引数

  * `β`: 有限体の要素

# 戻り値

  * `Array{F,1}`: 要素の共役の配列

# 例

```julia
julia> F4 = @GaloisField 2^2
julia> α = primitiveroot(F4)
julia> get_conjugates(α)
2-element Array{GaloisField{2,2},1}:
 α
 α^2
```

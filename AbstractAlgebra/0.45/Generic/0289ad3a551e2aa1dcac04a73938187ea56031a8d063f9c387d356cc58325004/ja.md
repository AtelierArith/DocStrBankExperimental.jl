```
conj(part::Partition)
```

`part`の共役部分を返します。すなわち、`part`のヤング図が主対角線を通して反射された部分です。

# 例

```jldoctest
julia> p = Partition([4,2,1,1,1])
4₁2₁1₃

julia> conj(p)
5₁2₁1₂
```

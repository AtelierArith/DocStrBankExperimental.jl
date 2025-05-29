```julia
subset(nt, s)

```

引数`s`で`nt`を部分集合にします。

# 例

```julia
julia> subset( (a = 1., b = 2., c = 3.), (:a, :b) )
(a = 1., b = 2.)
```

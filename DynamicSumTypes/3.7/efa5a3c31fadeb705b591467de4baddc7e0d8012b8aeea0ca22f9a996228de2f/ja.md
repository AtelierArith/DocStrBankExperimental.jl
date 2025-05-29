```
variant_constructor(instance)
```

インスタンスのコンストラクタを、`typeof(inst)'[kindof(inst)]`を使うよりも効率的に返します：

```julia
julia> @sum_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> a = AB'.A(1)
AB'.A(1)

julia> typeof(a)'[kindof(a)]
AB'.A

julia> variant_constructor(a)
AB'.A
```

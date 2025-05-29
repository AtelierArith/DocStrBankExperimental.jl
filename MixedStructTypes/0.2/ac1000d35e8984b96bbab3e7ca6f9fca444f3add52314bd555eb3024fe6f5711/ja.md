```
kindof(instance)
```

インスタンスの概念的な型を表すシンボルを返します：

```julia
julia> @compact_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> a = A(1);

julia> kindof(a)
:A
```

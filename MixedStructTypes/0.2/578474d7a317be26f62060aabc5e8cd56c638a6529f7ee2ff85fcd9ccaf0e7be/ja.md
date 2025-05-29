```
kindconstructor(instance)
```

インスタンスのコンストラクタを返します：

```julia
julia> @compact_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> a = A(1);

julia> kindconstructor(a)
A
```

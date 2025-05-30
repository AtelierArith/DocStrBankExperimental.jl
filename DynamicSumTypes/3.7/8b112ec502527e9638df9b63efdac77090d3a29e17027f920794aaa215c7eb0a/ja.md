```
@pattern(function_definition)
```

このマクロは、[`@sum_structs`](@ref)によって作成された型にパターンマッチを行うことを可能にします。

注意点として、このマクロ内の種類がそれらを含む他の型でラップされていない場合にのみ機能します。

## 例

```julia
julia> @sum_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> @pattern f(::AB'.A) = 1;

julia> @pattern f(::AB'.B) = 2;

julia> @pattern f(::Vector{AB}) = 3; # これは機能します 

julia> @pattern f(::Vector{AB'.B}) = 3; # これは機能しません
ERROR: LoadError: 他の型でラップされたバリアントにディスパッチすることはできません
...

julia> f(AB'.A(0))
1

julia> f(AB'.B(0))
2

julia> f([AB'.A(0), AB'.B(0)])
3
```

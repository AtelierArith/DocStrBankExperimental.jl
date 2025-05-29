```
@dispatch(function_definition)
```

このマクロは、[`@compact_structs`](@ref) または [`@sum_structs`](@ref) によって作成された型に対してディスパッチを行うことを可能にします。このマクロ内の型がそれらを含む任意の型でラップされていない場合にのみ機能することに注意してください。

## 例

```julia
julia> @compact_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> @dispatch f(::A) = 1;

julia> @dispatch f(::B) = 2;

julia> @dispatch f(::Vector{B}) = 3; # これは機能しません
ERROR: UndefVarError: `B` not defined
Stacktrace:
 [1] top-level scope
   @ REPL[7]:1

julia> f(A(0))
1

julia> f(B(0))
2
```

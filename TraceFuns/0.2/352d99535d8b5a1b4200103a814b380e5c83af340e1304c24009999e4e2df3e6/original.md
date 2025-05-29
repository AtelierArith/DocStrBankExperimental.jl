```
tracing(funs...) do
    expr
end
```

Trace all calls of the listed `funs` during evaluation of `expr`.

# Examples

```julia-repl
julia> fac(n) = if n < 1; 1 else n * fac(n - 1) end
fac (generic function with 1 method)

julia> tracing(Base, fac) do
           fac(2)
       end
0: fac(2) -- Method fac(n) @ Main REPL[25]:1 of fac
   1: <(2, 1) -- Method <(x::T, y::T) where T<:Union{Int128, Int16, Int32, Int64, Int8} @ Base int.jl:83 of <
   1: <(2, 1) -> false
   1: -(2, 1) -- Method -(x::T, y::T) where T<:Union{Int128, Int16, Int32, Int64, Int8, UInt128, UInt16, UInt32, UInt64, UInt8} @ Base int.jl:86 of -
   1: -(2, 1) -> 1
   1: fac(1) -- Method fac(n) @ Main REPL[25]:1 of fac
       2: <(1, 1) -- Method <(x::T, y::T) where T<:Union{Int128, Int16, Int32, Int64, Int8} @ Base int.jl:83 of <
       2: <(1, 1) -> false
       2: -(1, 1) -- Method -(x::T, y::T) where T<:Union{Int128, Int16, Int32, Int64, Int8, UInt128, UInt16, UInt32, UInt64, UInt8} @ Base int.jl:86 of -
       2: -(1, 1) -> 0
       2: fac(0) -- Method fac(n) @ Main REPL[25]:1 of fac
           3: <(0, 1) -- Method <(x::T, y::T) where T<:Union{Int128, Int16, Int32, Int64, Int8} @ Base int.jl:83 of <
           3: <(0, 1) -> true
       2: fac(0) -> 1
       2: *(1, 1) -- Method *(x::T, y::T) where T<:Union{Int128, Int16, Int32, Int64, Int8, UInt128, UInt16, UInt32, UInt64, UInt8} @ Base int.jl:88 of *
       2: *(1, 1) -> 1
   1: fac(1) -> 1
   1: *(2, 1) -- Method *(x::T, y::T) where T<:Union{Int128, Int16, Int32, Int64, Int8, UInt128, UInt16, UInt32, UInt64, UInt8} @ Base int.jl:88 of *
   1: *(2, 1) -> 2
0: fac(2) -> 2
2
```

See [`@trace`](@ref) for further details.

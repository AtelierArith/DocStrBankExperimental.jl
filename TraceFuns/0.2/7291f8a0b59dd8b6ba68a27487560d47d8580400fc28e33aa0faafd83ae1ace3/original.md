```
@trace expr [funs...]
```

Trace all calls of the listed `funs` during evaluation of `expr`. If `funs` includes the symbol `:all` all function calls are traced. If `funs` includes one or more modules, all functions from the corresponding modules are traced. 

# Examples

```julia-repl
julia> @trace 1 + 2 Base.:+
0: +(1, 2) -- Method +(x::T, y::T) where T<:Union{Int128, Int16, Int32, Int64, Int8, UInt128, UInt16, UInt32, UInt64, UInt8} @ Base int.jl:87 of +
0: +(1, 2) -> 3
3
```

Be careful using `:all` as the output may be long ...

```julia-repl
julia> @trace 1 * 2.0 :all
0: *(1, 2.0) -- Method *(x::Number, y::Number) @ Base promotion.jl:411 of *
   1: promote(1, 2.0) -- Method promote(x, y) @ Base promotion.jl:379 of promote
      ... long output clipped ...
   1: promote(1, 2.0) -> (1.0, 2.0)
   1: *(1.0, 2.0) -- Method *(x::T, y::T) where T<:Union{Float16, Float32, Float64} @ Base float.jl:410 of *
       2: mul_float(1.0, 2.0) -- Method IntrinsicFunction(...) @ Core none:0 of mul_float
       2: mul_float(1.0, 2.0) -> 2.0
   1: *(1.0, 2.0) -> 2.0
0: *(1, 2.0) -> 2.0
2.0
```

Tracing nicely illustrates recursive functions

```julia-repl
julia> fibo(n::Integer) = if n < 2 1 else fibo(n-1) + fibo(n-2) end
fibo (generic function with 1 method)

julia> @trace fibo(3) fibo
0: fibo(3) -- Method fibo(n::Integer) @ Main REPL[3]:1 of fibo
   1: fibo(2) -- Method fibo(n::Integer) @ Main REPL[3]:1 of fibo
       2: fibo(1) -- Method fibo(n::Integer) @ Main REPL[3]:1 of fibo
       2: fibo(1) -> 1
       2: fibo(0) -- Method fibo(n::Integer) @ Main REPL[3]:1 of fibo
       2: fibo(0) -> 1
   1: fibo(2) -> 2
   1: fibo(1) -- Method fibo(n::Integer) @ Main REPL[3]:1 of fibo
   1: fibo(1) -> 1
0: fibo(3) -> 3
3
```

See also [`tracing`](@ref) for the functional interface.

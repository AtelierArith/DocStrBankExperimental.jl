```
trace_test(W::WitnessSet; options...)
```

Performs a trace test [^LRS18] to verify whether the given witness set `W` is complete. Returns the trace of the witness set which should be theoretically be 0 if `W` is complete. Due to floating point arithmetic this is not the case, thus is has to be manually checked that the trace is sufficiently small. Returns `nothing` if the trace test failed due to path tracking failures. The `options` are the same as for calls to [`witness_set`](@ref).

```julia-repl
julia> @var x y;
julia> F = System([x^2 + y^2 - 5], [x, y])
System of length 1
 2 variables: x, y

 -5 + x^2 + y^2

julia> W = witness_set(F)
Witness set for dimension 1 of degree 2

julia> trace = trace_test(W)
9.981960497718987e-16
```

[^LRS18]: Leykin, Anton, Jose Israel Rodriguez, and Frank Sottile. "Trace test." Arnold Mathematical Journal 4.1 (2018): 113-125.

APA

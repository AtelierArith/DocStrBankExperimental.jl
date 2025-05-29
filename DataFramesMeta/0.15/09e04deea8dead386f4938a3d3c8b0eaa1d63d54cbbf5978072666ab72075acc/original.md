```
@kwarg(args...)
```

Inside of DataFramesMeta.jl macros, pass keyword arguments to the underlying DataFrames.jl function when arguments are written in "block" format.

```
julia> df = DataFrame(x = [1, 1, 2, 2], b = [5, 6, 7, 8]);

julia> @rsubset df begin
           :x == 1
           @kwarg view = true
       end
2×2 SubDataFrame
 Row │ x      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      5
   2 │     1      6
```

!!! note
    This only has meaning inside DataFramesMeta.jl macros. It does not work outside of DataFrames.jl macros.


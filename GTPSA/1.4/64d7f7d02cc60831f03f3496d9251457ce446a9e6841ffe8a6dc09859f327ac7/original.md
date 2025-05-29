```
@FastGTPSA(expr_or_block)
```

Macro to speed up evaluation of mathematical expressions containing TPSs. The temporaries generated during evaluation of the expression are drawn  from a thread-safe buffer, reducing the number of heap allocations to  2 (which is for a single TPS) for the result. @FastGTPSA is completely  transparent to all other types, so it can be prepended to expressions  while still maintaining type-generic code.

```julia-repl
julia> using GTPSA, BenchmarkTools

julia> d = Descriptor(3,7); Δx = @vars(d);

julia> t = @btime $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
  3.458 μs (20 allocations: 11.88 KiB)

julia> t = @btime @FastGTPSA $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
  3.172 μs (2 allocations: 1.94 KiB)
```

`@FastGTPSA` can also be prepended to a block of code, in which case it  is applied after every `=` sign in the block: 

```julia-repl
julia> @btime @FastGTPSA begin
       t1 = $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
       t2 = $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
       a = t1+t2
       L = 5+3*exp(7)
       end
  6.317 μs (6 allocations: 5.81 KiB)
```

Broadcasting is also compatible with `@FastGTPSA` (note two allocations  per `TPS` and one allocation per `Array`):

```julia-repl
julia> using GTPSA, BenchmarkTools

julia> d = Descriptor(3, 7); Δx = @vars(d); y = rand(3);

julia> @btime @FastGTPSA begin
        out = @. $Δx^3*sin($y)/log(2+$x)-exp($x*$y)*im;
       end;
  7.573 μs (7 allocations: 5.89 KiB)
```

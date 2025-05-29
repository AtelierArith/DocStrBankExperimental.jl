```
@FastGTPSA!(expr_or_block)
```

Macro to speed up evaluation of mathematical expressions that may contain assignment to pre-allocated `TPS`s. The temporaries generated during  evaluation of the expression are drawn from a thread-safe buffer. With this  macro, the number of heap allocations during evaluation of expressions  containing `TPS`s is 0, and it is fully transparent to non-TPS types.

This macro supports assignment using `=`, `+=`, `-=`, `*=`, `/=`, and `^=`.

**Important:** The symbols must be defined prior to calling the macro  regardless of whether or not the type is a `TPS`:

```julia-repl
julia> using GTPSA, BenchmarkTools

julia> d = Descriptor(3,7); Δx = @vars(d); 

julia> t = ComplexTPS64(); # Pre-allocate

julia> @btime @FastGTPSA! $t = $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
  2.972 μs (0 allocations: 0 bytes)

julia> @btime @FastGTPSA! $t ^= $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
  6.550 μs (0 allocations: 0 bytes)

julia> y = rand(3); z = 2; # transparent to non-TPS types 

julia>  @btime @FastGTPSA! $z = $y[1]^3*sin($y[2])/log(2+$y[3])-exp($y[1]*$y[2])*im;
  11.344 ns (0 allocations: 0 bytes)
```

Like `@FastGTPSA`, `@FastGTPSA!` can prepended to a block of code, in  which case it is applied before every line in the block containing assignment:

```julia-repl
julia> t1 = zero(ComplexTPS64); t2 = zero(ComplexTPS64); z = 0; 

julia> @btime @FastGTPSA! begin
       $t1 = $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
       $t2 -= $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
       $z += 7
       end
  5.965 μs (0 allocations: 0 bytes)
```

Broadcasting is also compatible with `@FastGTPSA!`:

```julia-repl
julia> using GTPSA, BenchmarkTools

julia> d = Descriptor(3, 7); Δx = @vars(d); y = rand(3);

julia> out = zeros(ComplexTPS64, 3) # pre-allocate

julia> @btime @FastGTPSA! begin
        @. $out = $Δx^3*sin($y)/log(2+$Δx)-exp($Δx*$y)*im;
       end;
  7.312 μs (0 allocations: 0 bytes)
```

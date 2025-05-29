```
val = gzero(sys; fast = false, prescale, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ)
```

Return for the descriptor system `sys = (A-λE,B,C,D)` the complex vector `val` containing the  finite and infinite Smith zeros of the system matrix pencil  

```
           | A-λE | B | 
   S(λ) := |------|---| .
           |  C   | D |
```

The values in `val` are called the *invariant zeros* of the pencil `S(λ)` and are the *transmission zeros* of the  transfer function matrix of `sys` if `A-λE` is *regular* and the descriptor system realization  `sys = (A-λE,B,C,D)` is *irreducible*.

If `prescale = true`, a preliminary balancing of the descriptor system matrices is performed.  The default setting is `prescale = gbalqual(sys) > 10000`, where `gbalqual(sys)` is the  scaling quality of the descriptor system model `sys` (see [`gbalqual`](@ref)). 

The computation of the zeros is performed by reducing the pencil `S(λ)` to an appropriate Kronecker-like form   using orthonal similarity transformations and involves rank decisions based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. 

The keyword arguements `atol1`, `atol2`  and `rtol` specify the absolute tolerance for the nonzero elements of `A`, `B`, `C` and `D`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance for the nonzero elements of `A`, `E`, `B`, `C` and `D`, respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of `A`, and `ϵ` is the  working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 

hlu!(A::AbstractMatrix{T}) where {T} Return LU factorization of A

C. T. Kelley, 2023

This function is a hack of generic_lufact! which is part of

https://github.com/JuliaLang/julia/blob/master/stdlib/LinearAlgebra/src/lu.jl

I "fixed" the code to be Float16 only and fixed pivoting to only MaxRow.

All I did in the factorization was thread the critical loop with FLoops.@floop and put @simd in the inner loop. For larger problems (n > 128) these changes got me a 2-10x speedup on my Mac M2 Pro with 8 performance cores. I'm happy.

```
 pschur!(A::Array{Float64,3}, ilh::Tuple(Int,Int) = (1, size(A,1)); kwargs...) -> (S, Z, ihess)
```

Same as `pschur(A; kwargs...)` but uses the input matrix `A` as workspace and specifies a range `ilh = (ilo, ihi)`, such that all matrices `A(j), j = 1, ..., p`, are already in periodic Schur forms in rows and columns `1:ilo-1` and `ihi+1:n`, where `n` is the first dimension of `A`.

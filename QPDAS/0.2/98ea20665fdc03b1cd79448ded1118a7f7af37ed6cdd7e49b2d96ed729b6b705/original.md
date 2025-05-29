b, projection = ldiv2!(F::CholeskySpecialShifted{T,MT}, b::AbstractVector{T}; x0=zero(T))

Solve `Mx=b` where F is Cholesky factorization if M with some rows and columns set to identity

The solution `x` is the projection onto `Mx=b` from `x0`. `x0` can be a Vector or Number (treated as `fill(x0,n)`).

If no solution exists, finds projection of `b` onto space `Mx=0`.

`projection=false` if soulution `Mx=b` found, and `projection=true` if not.

Overwrites and returns `b`.

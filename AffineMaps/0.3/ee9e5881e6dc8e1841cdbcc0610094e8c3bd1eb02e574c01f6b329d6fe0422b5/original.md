muladd(f.A, x, f.b)     struct InvAddMul

`f = InvAddMul(A, b)` has the behavior `f(x) == (f.A \ x) .- f.b`. It is the inverse of `AddMul(A, b)`.

See [`AbstractAffineMap`](@ref) for more information.

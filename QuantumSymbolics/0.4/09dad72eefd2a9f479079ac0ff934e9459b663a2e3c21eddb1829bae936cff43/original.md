Dagger, i.e., adjoint of quantum objects (kets, bras, operators).

```jldoctest
julia> @ket a; @op A;

julia> dagger(2*im*A*a)
(0 - 2im)|a⟩†A†

julia> @op B;

julia> dagger(A*B)
B†A†

julia> ℋ = SHermitianOperator(:ℋ); U = SUnitaryOperator(:U);

julia> dagger(ℋ)
ℋ

julia> dagger(U)
U⁻¹
```

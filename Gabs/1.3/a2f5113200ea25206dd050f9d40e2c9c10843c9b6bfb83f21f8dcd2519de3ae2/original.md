```
issymplectic(basis::SymplecticBasis, x::T)
```

Check if input matrix satisfies symplectic definition.

## Example

```jldoctest
julia> basis = QuadPairBasis(1);

julia> issymplectic(basis, [1.0 0.0; 0.0 1.0])
true
```

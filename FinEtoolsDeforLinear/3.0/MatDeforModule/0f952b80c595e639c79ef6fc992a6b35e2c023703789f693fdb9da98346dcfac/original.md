```
tens4ijkl!(t::Array{T, 4}, A::FA, B::FB, op = :+) where {T, FA, FB}
```

Fill a 4th-order tensor as a dyadic product of two 2nd-order tensors.

The `i,j,k,l` component is given as `t[i,j,k,l]=A(i,j)*B(k,l)`.

!!! note



The tensor is accumulated to. It needs to be initialized to zero, if that is desired as the initial state.

# Example

```
t = fill(0.0, 3, 3, 3, 3)
delta = (I, J) -> I == J ? 1.0 : 0.0
tens4ijkl!(t, delta, delta)
S = rand(3, 3)
@show tr(S) * I
tS = fill(0.0, 3, 3)
@show tens4dot2!(tS, t, S)
```

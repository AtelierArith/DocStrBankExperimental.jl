```
tens4ikjl!(t::Array{T, 4}, A::FA, B::FB) where {T, FA, FB}
```

Fill a 4th-order tensor as a dyadic product of two 2nd-order tensors.

The `i,j,k,l` component is given as `t[i,j,k,l]=A(i,k)*B(j,l)`.

!!! note



The tensor is accumulated to. It needs to be initialized to zero, if that is desired as the initial state.

# Example

```
t = fill(0.0, 3, 3, 3, 3)
delta = (I, J) -> I == J ? 1.0 : 0.0
tens4ikjl!(t, delta, delta)
S = rand(3, 3)
@show transpose(S) 
tS = fill(0.0, 3, 3)
@show transpose(S) - tens4dot2!(tS, t, S)
```

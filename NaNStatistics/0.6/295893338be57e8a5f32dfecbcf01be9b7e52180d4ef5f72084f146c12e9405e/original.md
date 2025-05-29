```julia
nanlogcumsumexp(A)
```

Return the logarithm of the cumulative sum of `exp.(A)` – i.e., `log.(cumsum.(exp.(A)))`, but ignoring `NaN`s and avoiding numerical over/underflow. As `nancumsum`, but operating on logarithms; as `nanlogsumexp`, but returning a array of cumulative sums, rather than a single value.

## Examples

```julia

```

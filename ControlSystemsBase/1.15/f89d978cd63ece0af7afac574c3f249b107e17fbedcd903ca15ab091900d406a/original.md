```
delay(tau)
delay(tau, Ts)
delay(T::Type{<:Number}, tau)
delay(T::Type{<:Number}, tau, Ts)
```

Create a pure time delay of length `τ` of type `T`.

The type `T` defaults to `promote_type(Float64, typeof(tau))`.

If `Ts` is given, the delay is discretized with sampling time `Ts` and a discrete-time StateSpace object is returned.

# Example:

Create a LTI system with an input delay of `L`

```julia
L = 1
tf(1, [1, 1])*delay(L)
s = tf("s")
tf(1, [1, 1])*exp(-s*L) # Equivalent to the version above
```

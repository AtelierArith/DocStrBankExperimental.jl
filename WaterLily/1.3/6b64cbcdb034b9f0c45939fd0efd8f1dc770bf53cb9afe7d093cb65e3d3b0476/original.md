```
AbstractBody
```

Immersed body Abstract Type. Any `AbstractBody` subtype must implement

```
d = sdf(body::AbstractBody, x, t=0)
```

and

```
d,n,V = measure(body::AbstractBody, x, t=0, fastd²=Inf)
```

where `d` is the signed distance from `x` to the body at time `t`, and `n` & `V` are the normal and velocity vectors implied at `x`. A fast-approximate method can return `≈d,zero(x),zero(x)` if `d^2>fastd²`.

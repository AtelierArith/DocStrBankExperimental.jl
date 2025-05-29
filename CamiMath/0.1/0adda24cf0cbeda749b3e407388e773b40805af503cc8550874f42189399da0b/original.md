```
texp(x::T, a::T, p::Int) where T <: Real
```

Truncated exponential: Taylor expansion of $exp(x)$ about $x = a$  up to order `p`,

$$
    \mathsf{texp}(x,a,p) = 1+(x-a)+\frac{1}{2}(x-a)^2+⋯+\frac{1}{p!}(x-a)^p
$$

### Examples:

```
julia> texp(1.0, 0.0, 5)
2.7166666666666663

julia> texp(1, 0, 5)
163//60
```

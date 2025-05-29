```
texp(x::T, a::T, p::Int) where T <: Real
```

切断指数関数: $exp(x)$ のテイラー展開を $x = a$ の周りで、次数 `p` まで行います。

$$
    \mathsf{texp}(x,a,p) = 1+(x-a)+\frac{1}{2}(x-a)^2+⋯+\frac{1}{p!}(x-a)^p
$$

### 例:

```
julia> texp(1.0, 0.0, 5)
2.7166666666666663

julia> texp(1, 0, 5)
163//60
```

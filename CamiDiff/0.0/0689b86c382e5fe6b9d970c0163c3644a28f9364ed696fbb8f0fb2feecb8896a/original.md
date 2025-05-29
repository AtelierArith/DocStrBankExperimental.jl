```
create_adams_moulton_weights(k::Int [; rationalize=false [, devisor=false [, T=Int]]])
```

$k^{th}$-order Adams-Moulton weights vector $a^k \equiv[a_k^k,⋯\ a_0^k]$.   Note the *reversed* vector ordering, which is the order of use in the summation below,

$$
y[n+1] = y[n] + \frac{1}{D}\sum_{j=0}^{k}a^k[j]f[n+1-k+j],
$$

where $a^k[j] \equiv a_{k-j}^k$. The $a_j^k$ are the Adams-Moulton weight coefficients and $D$ is the corresponding Adams-Moulton divisor. By default the output is in Float64, optionally the output is rational,  with or without specification of the gcd devisor.

#### Example:

```
julia> [create_adams_moulton_weights(k; rationalize=true, devisor=true, T=Int) for k=1:5]
8-element Vector{Tuple{Int64, Int64, Vector{Int64}}}:
 (1, 2, [1, 1])
 (2, 12, [-1, 8, 5])
 (3, 24, [1, -5, 19, 9])
 (4, 720, [-19, 106, -264, 646, 251])
 (5, 1440, [27, -173, 482, -798, 1427, 475])

julia> k = 5;
julia> w = create_adams_moulton_weights(k; rationalize=true, devisor=true); println(w)
(5, 1440, [27, -173, 482, -798, 1427, 475])

julia> w = create_adams_moulton_weights(k; rationalize=true, devisor=false); println(w)
Rational{Int64}[3//160, -173//1440, 241//720, -133//240, 1427//1440, 95//288]

julia> w = create_adams_moulton_weights(k; rationalize=false); println(w)
[0.01875, -0.12013888888888889, 0.3347222222222222, -0.5541666666666667, 0.9909722222222223, 0.3298611111111111]
```

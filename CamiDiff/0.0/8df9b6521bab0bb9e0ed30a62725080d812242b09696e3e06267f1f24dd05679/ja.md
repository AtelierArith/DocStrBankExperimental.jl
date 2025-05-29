```
create_adams_bashford_weights(k::Int [; rationalize=false [, devisor=false [, T=Int]]])
```

$$
k^{th}
$$

-階アダムス-バシュフォード重みベクトル $b^k \equiv[b_k^k,⋯\ b_0^k]$。下記の合計での使用順序に対応する*逆順*に注意してください。

$$
y[n+1] = y[n] + \frac{1}{D}\sum_{j=0}^{k}b^k[j]f[n+1-k+j],
$$

ここで $b^k[j] \equiv b_{k-j}^k$ です。$b_j^k$ はアダムス-バシュフォード重み係数で、$D$ は対応するアダムス-モールトン除数です。デフォルトでは出力はFloat64ですが、オプションで出力は有理数であり、gcd除数の指定の有無にかかわらず可能です。

#### 例:

```
julia> [create_adams_bashford_weights(k; rationalize=true, devisor=true, T=Int) for k=1:5]
8-element Vector{Tuple{Int64, Int64, Vector{Int64}}}:
 (1, 2, [-1, 3])
 (2, 12, [5, -16, 23])
 (3, 24, [-9, 37, -59, 55])
 (4, 720, [251, -1274, 2616, -2774, 1901])
 (5, 1440, [-475, 2877, -7298, 9982, -7923, 4277])

julia> k = 5;

julia> w = create_adams_bashford_weights(k; rationalize=true, devisor=true); println(w)
(5, 1440, [-475, 2877, -7298, 9982, -7923, 4277])

julia> w = create_adams_bashford_weights(k; rationalize=true, devisor=false); println(w)
Rational{Int64}[-95//288, 959//480, -3649//720, 4991//720, -2641//480, 4277//1440]

julia> w = create_adams_bashford_weights(k; rationalize=false); println(w)
[-0.3298611111111111, 1.9979166666666666, -5.0680555555555555, 6.9319444444444445, -5.502083333333333, 2.970138888888889]
```

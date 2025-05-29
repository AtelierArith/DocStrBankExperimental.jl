```
fdiff_adams_bashford_expansion_coeff(k::Int [; T=Int [, msg=true]])
fdiff_adams_bashford_expansion_polynom(k::Int [; T=Int [, msg=true]])
```

$$
(k+1)
$$

-点アダムス-バシュフォード展開係数 $B_k \equiv [B_0^k,⋯\ B_k^k]$。下記の総和での使用順序である*前方*ベクトル順序に注意してください、

$$
-\frac{∇}{(1-∇)ln(1-∇)}=\sum_{p=0}^{\infty}B_p∇^p=1+\ \frac{1}{2}∇+\ \frac{5}{12}∇^2+\ ⋯.
$$

#### 例:

```
julia> o = fdiff_adams_bashford_expansion_polynom(5); println(o)
Rational{Int64}[1, 1//2, 5//12, 3//8, 251//720, 95//288]

julia> fdiff_adams_bashford_expansion_coeff(0)
1//1

julia> fdiff_adams_bashford_expansion_coeff(5)
95//288

julia> fdiff_adams_bashford_expansion_coeff(20)
Integer-overflow protection: output converted to BigInt
8136836498467582599787//33720021833328230400000
```

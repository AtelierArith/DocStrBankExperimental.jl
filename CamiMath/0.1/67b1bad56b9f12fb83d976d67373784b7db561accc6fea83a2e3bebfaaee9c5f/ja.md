```
faulhaber_summation(n::Integer, p::Int [; msg=true])
```

最初の $n$ 自然数の $p^{th}$ 累乗の合計

$$
    \sum_{k=1}^{n}k^{p}=H_{n,-p}=F(n,p+1).
$$

ここで、$H_{n,-p}$ は `-p` の累乗の [`harmonicNumber`](@ref) であり、$F(n,p)$ は `p` の累乗の [`faulhaber_polynomial`](@ref) です。

  * `msg` : 整数オーバーフロー保護 (IOP) - 有効化時の警告

#### 例:

```
julia> faulhaber_summation(3,5)
276

julia> faulhaber_summation(3,60)
IOP capture: faulhaber_polynom autoconverted to Rational{BigInt}
42391158276369125018901280178
```

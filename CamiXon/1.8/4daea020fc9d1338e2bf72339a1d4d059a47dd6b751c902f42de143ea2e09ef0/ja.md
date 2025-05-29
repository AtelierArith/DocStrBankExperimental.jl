```
getNcut(f0::T, f::Vector{T}, start::Int, stop::Int) where T<:Real
getNcut(f0::T, f::Vector{T}, itr::UnitRange) where T<:Real
```

離散関数 $f[n]$ が区間 `start ≤ n ≤ stop` で値 $f_0$ と交差する点に対応するインデックスは、

$$
    f[n_{cut}] = f_0.
$$

条件: $f[n]$ は区間 `start ≤ n ≤ stop` で単調増加または単調減少でなければなりません。

注: 単調*減少*関数の場合、$n_{cut}$ は $f[n] > f_0$ となる*最大*の $n$ で近似されます。単調*増加*関数の場合、$n_{cut}$ は $f[n] > f_0$ となる*最小*の $n$ で近似されます。

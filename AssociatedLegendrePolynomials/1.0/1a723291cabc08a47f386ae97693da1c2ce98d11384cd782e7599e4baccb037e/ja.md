```
N = Nlm([T=Float64], l, m)
```

正規化定数を計算します

$$
    N_\ell^m \equiv \sqrt{\frac{2\ell+1}{4\pi} \frac{(\ell-m)!}{(\ell+m)!}}
$$

これは標準単位正規化された $P_\ell^m(x)$ に基づいて、球面調和関数の正規化された関数 $\lambda_\ell^m(x)$ を定義します

$$
    \lambda_\ell^m(x) \equiv N_\ell^m P_\ell^m(x)
$$

型 `T` の数を使用します。

[`Plm`](@ref) および [`λlm`](@ref) も参照してください。

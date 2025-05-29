```
FCoeffs{A, B}(fnlm::Dict{Tuple{Int64,Int64,Int64}, A},
    radial_basis::B)
```

$$
\langle f | n \ell m \rangle
$$

係数を`(n,ell,m) => f_nlm`として辞書に格納し、それらを計算するために使用された放射基を格納します。角部分には球面調和関数が使用されたと仮定します。`A`は`fnlm`係数を格納する辞書の要素型（`Float64`または`Measurement`のいずれかであるべきです）。`B`は放射基の型です。

```
cyclotomic(n::Int, x::ZZPolyRingElem)
```

$$
n
$$

番目の循環多項式を返します。これは$\Phi_n(x) = \prod_{\omega} (x-\omega)$として定義され、ここで$\omega$はすべての$n$番目の原始単位根を走ります。

```
ProjectF(f, nl_max::Tuple{Int,Int}, radial_basis::RadialBasis; 
         dict=false, use_measurements=false, integ_method=:cubature,
         integ_params=(;))
```

$$
\langle f | n \ell m \rangle
$$

を各 $(n,\ell,m)$ について `nl_max = (n_max, l_max)` まで評価し、結果を `ProjectedF` として返します。

`f` : `Function`、`f_uSph`、`GaussianF`、または `Vector{GaussianF}` であることができます。関数に対称性がある場合、かつガウスでない場合は `f_uSph` を使用することが推奨されます。これにより評価が大幅に高速化されます。

`radial_basis` : `Wavelet` または `Tophat` のいずれかです。

`dict` : `true` の場合、係数を辞書として保存する `FCoeffs` を返します。

`use_measurements` : `true` の場合、結果を不確実性を伴う測定値として提供します。これは積分誤差によって与えられます。

`integ_method` : `:discrete`、`:cubature`、`:vegas`、または `:vegasmc` のいずれかです。`:discrete` は `SphericalHaarTransform` を使用して、二点ガウス求積法で変換を行います。

`integ_params` : 積分器に渡すキーワード引数です。`:cubature` の場合、これらは `hcubature` のためのキーワード引数です。`:vegas` または `:vegasmc` の場合、これらは `MCIntegration` の `integrate` メソッドのためのキーワード引数です。`:discrete` を使用している場合は無視されます。

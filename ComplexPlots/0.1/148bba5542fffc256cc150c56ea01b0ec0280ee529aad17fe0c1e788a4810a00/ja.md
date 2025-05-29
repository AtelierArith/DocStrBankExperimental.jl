```
artist(base=exp(1), colormap=Makie.ColorSchemes.cyclic_mygbm_30_95_c78_n256)
```

`artist(b)` は、複素数 `z` を色にマッピングする関数を返します。色相は `z` の角度によって決まります。値（明るさ）は $\log_b |z|$ の小数部分によって決まります。任意のカラーマップを指定することもできますが、循環型のものを強く推奨します。

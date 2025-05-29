```julia
rmr0fromdpar(dpar)
```

`dpar`に対する`rmr0`を計算します。「マルチキネティック」アパタイトのフィッショントラックは、Ketcham et al. 1999の関係（図7b）に従います（doi: 10.2138/am-1999-0903）。

```
rmr0 = 1 - exp(0.647(dpar-1.75) - 1.834)
```

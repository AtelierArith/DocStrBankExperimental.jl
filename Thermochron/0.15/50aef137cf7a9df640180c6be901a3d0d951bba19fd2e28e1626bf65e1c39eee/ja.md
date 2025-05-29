```julia
rmr0fromcl(Cl)
```

塩素含量 `Cl` [APFU] に対する `rmr0` を計算します。これは Ketcham et al. 1999 (doi: 10.2138/am-1999-0903) の関係式 (図 7a) に基づく "マルチキネティック" アパタイト fission track に従います。

```
rmr0 = 1 - exp(2.107(1 - abs(Cl - 1)) - 1.834)
```

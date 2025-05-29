```
latent_heat_vaporization(Tair)
```

空気温度の関数としての蒸発潜熱 

$$
\lambda = (2.501 - 0.00237 \, Tair) 10^6
$$

。

# 引数:

  * Tair:  空気温度 (℃)

# 値

$$
\lambda
$$

: 蒸発潜熱 (J kg-1) 

# 参考文献

  * Stull, B*, 1988: An Introduction to Boundary Layer Meteorology (p*641)           Kluwer Academic Publishers, Dordrecht, Netherlands
  * Foken, T, 2008: Micrometeorology_ Springer, Berlin, Germany

```@example
latent_heat_vaporization.(5:5:45)        
```

```
law_of_refraction(n1, n2 = 1.0) -> t, r
```

Create transmission and refraction functions `t, r` that follow Snell's law, i.e. the transmission probability is set to 1.0 except for the case of total internal reflection. 

`n1` is the index of refraction for the `pflag = false` side of an obstacle, while `n2` is the index of refraction for `pflag = true`.

```
d,n,V = measure(body::AutoBody||Bodies,x,t;fastd²=Inf)
```

Determine the implicit geometric properties from the `sdf` and `map`. The gradient of `d=sdf(map(x,t))` is used to improve `d` for pseudo-sdfs. The velocity is determined *solely* from the optional `map` function. Skips the `n,V` calculation when `d²>fastd²`.

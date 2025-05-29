```
d,n,V = measure(body::AutoBody||Bodies,x,t;fastd²=Inf)
```

`sdf`と`map`から暗黙の幾何学的特性を決定します。`d=sdf(map(x,t))`の勾配は、擬似sdfのために`d`を改善するために使用されます。速度はオプションの`map`関数から*のみ*決定されます。`d²>fastd²`の場合、`n,V`の計算をスキップします。

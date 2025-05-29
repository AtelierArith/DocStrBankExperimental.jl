```
local_metric(M::Sphere{n}, p, ::DefaultOrthonormalBasis)
```

は、[`DefaultOrthonormalBasis`](@extref `ManifoldsBase.DefaultOrthonormalBasis`)における計量の局所表現を返します。具体的には、対角行列のサイズは $n×n$ で、対角上に1が配置されます。これは、計量が埋め込みから点 $p$ における接空間 $T_p\mathcal M$ への制限によって得られるためです。

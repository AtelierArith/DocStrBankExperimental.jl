```
added_mass(panels;kwargs...)
```

追加質量行列 mᵢⱼ = -∫ₛ Φᵢ(x) nⱼ da のための `panels` のセット、ここで Φᵢ は方向 i の単位運動によるポテンシャルです。計算は `Threads.nthreads()>1` の場合にマルチスレッドで加速されます。

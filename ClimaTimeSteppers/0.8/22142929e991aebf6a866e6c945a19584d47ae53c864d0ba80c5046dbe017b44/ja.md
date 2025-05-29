```
Multirate(fast, slow)
```

`fast`と`slow`アルゴリズムを組み合わせたマルチレートルンゲ–クッタ法

`slow`は以下の関数のメソッドを提供する任意のアルゴリズムであることができます

  * `init_inner(prob, outercache, dt)`
  * `update_inner!(innerinteg, outercache, f_slow, u, p, t, dt, stage)`

現在これをサポートしているアルゴリズムは：

  * [`LowStorageRungeKutta2N`](@ref)
  * [`MultirateInfinitesimalStep`](@ref)
  * [`WickerSkamarockRungeKutta`](@ref)

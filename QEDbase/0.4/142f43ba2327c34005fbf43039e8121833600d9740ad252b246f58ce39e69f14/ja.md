```
outgoing_particles(proc_def::AbstractProcessDefinition)
```

散乱プロセスのインターフェース関数。与えられたプロセス定義に対する出力粒子のタプルを返します。この関数は散乱プロセスインターフェースを実装するために必要です。

!!! note "パフォーマンス"
    この関数がコンパイル時に既知の値を返す場合、派生関数のパフォーマンスに非常に有益です。


参照: [`AbstractParticleType`](@ref)

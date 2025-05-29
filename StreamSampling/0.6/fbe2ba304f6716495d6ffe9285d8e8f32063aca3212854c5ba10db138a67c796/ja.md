```
ReservoirSample{T}([rng], method = AlgRSWRSKIP())
ReservoirSample{T}([rng], n::Int, method = AlgL(); ordered = false)
```

リザーバサンプルを初期化します。これにより、[`fit!`](@ref)でフィッティングすることができます。最初のシグネチャは、単一の要素のみが収集されるサンプルを表します。`ordered`がtrueの場合、リザーバサンプルの値は、[`ordvalue`](@ref)を使用して収集された順序で取得できます。

サポートされているメソッドについては、[`Sampling Algorithms`](@ref)セクションを参照してください。

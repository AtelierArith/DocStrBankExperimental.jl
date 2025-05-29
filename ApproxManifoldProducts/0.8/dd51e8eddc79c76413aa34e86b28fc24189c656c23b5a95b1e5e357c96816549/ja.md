```julia
mmd!(MF, val, a, b; ...)
mmd!(MF, val, a, b, N; ...)
mmd!(MF, val, a, b, N, M; ...)
mmd!(MF, val, a, b, N, M, threads; bw)

```

MMDの不均衡（すなわち「距離」）測定は、2つの信念間のカーネルヒルベルト埋め込みに基づいています。

ノート：

  * これはインプレースバージョンです（mmdよりもインプレースです）

開発ノート：

  * TODO 同じ重みの粒子を仮定しない
  * TODO SIMDとSLEEFのプロファイル
  * TODO メモリを最適化
  * TODO マルチスレッド化する

参照： [`mmd`](@ref), [`ker`](@ref)

```julia
sampleFactor(cf)
sampleFactor(cf, N)

```

因子確率モデルを `N::Int` 回サンプリングし、サンプルを事前に割り当てられた `ccw.measurement` コンテナに格納します。

DevNotes

  * 可能な限りインプレース操作を使用し、`measurement` は `::Tuple` であることを忘れないでください。
  * TODO 現在は `.threadid()==1` のみで動作します。#1094 を参照してください。
  * また、JuliaRobotics/RoME.jl#465 も参照してください。

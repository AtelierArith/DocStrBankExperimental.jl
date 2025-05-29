```
ImmiscibleSystem(phases; reference_densities = ones(length(phases)))
ImmiscibleSystem((LiquidPhase(), VaporPhase()), reference_densities = (1000.0, 700.0))
```

不混和流体システム: 各成分は単一の相にのみ存在し、成分の数は相の数と等しい。

与えられた相に対して不混和システムを設定し、オプションの参照密度を指定します。このシステムは、デフォルトの主要変数として[Pressure](@ref)と[Saturations](@ref)を使用することで簡単に指定できます。不混和システムは、相間での質量移動がないこと、そして相が組成において均一であることを前提としています。

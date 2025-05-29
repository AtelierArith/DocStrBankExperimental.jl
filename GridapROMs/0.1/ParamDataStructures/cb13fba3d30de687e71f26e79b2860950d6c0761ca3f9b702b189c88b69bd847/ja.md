```
abstract type TransientRealization{P<:Realization,T<:Real} <: AbstractRealization end
```

時間的パラメトリック実現を表します。すなわち、時間範囲内の各時間ステップに対して与えられたパラメータ空間から抽出されたサンプルです。このタイプの最も明白な応用は、初期条件が与えられる過渡的PDEです。この慣例に従い、初期時間瞬間は他の時間ステップとは別に保持されます。

```
integrate!(tseq::TimeSequence)
```

`tseq`に格納された値を台形法を使用して時間に沿って積分します。新しい値は`tseq`に書き込まれます。最初の値はゼロに設定されます。

## 例

```jldoctest
julia> using LatticeModels

julia> tseq = TimeSequence(0:0.1:10, 0:0.1:10)  # f(t) = t
TimeSequence{Float64} with 101 entry
Timestamps in range 0.0 .. 10.0:
  0.0 => 0.0
  0.1 => 0.1
  0.2 => 0.2
  0.3 => 0.3
  0.4 => 0.4
  0.5 => 0.5
  0.6 => 0.6
  0.7 => 0.7
  0.8 => 0.8
  ⋮

julia> integrate!(tseq)                         # F(t) = t^2 / 2
TimeSequence{Float64} with 101 entry
Timestamps in range 0.0 .. 10.0:
  0.0 => 0.0
  0.1 => 0.005
  0.2 => 0.02
  0.3 => 0.045
  0.4 => 0.08
  0.5 => 0.125
  0.6 => 0.18
  0.7 => 0.245
  0.8 => 0.32
  ⋮
```

```
`tseq`に格納された値を対称差分公式を使用して時間で微分します。新しい値は`tseq`に書き込まれます。

## 例

```

jldoctest julia> using LatticeModels

julia> tseq = TimeSequence(0:0.1:10, 0:0.1:10)  # f(t) = t TimeSequence{Float64} with 101 entry Timestamps in range 0.0 .. 10.0:   0.0 => 0.0   0.1 => 0.1   0.2 => 0.2   0.3 => 0.3   0.4 => 0.4   0.5 => 0.5   0.6 => 0.6   0.7 => 0.7   0.8 => 0.8   ⋮

julia> differentiate!(tseq)                     # f'(t) = 1 TimeSequence{Float64} with 100 entries Timestamps in range 0.05 .. 9.95:   0.05 => 1.0   0.15 => 1.0   0.25 => 1.0   0.35 => 1.0   0.45 => 1.0   0.55 => 1.0   0.65 => 1.0   0.75 => 1.0   0.85 => 1.0   ⋮ ```

```
𝐶
```

`𝐶` (𝐶 = `\itC+tab`) は、使用する準備が整ったデフォルトの時計です。

# 例

```jldoctest
julia> using DiscreteEvents

julia> resetClock!(𝐶)
"clock reset to t₀=0.0, sampling rate Δt=0.01."

julia> 𝐶  # default clock
Clock 1: state=:idle, t=0.0, Δt=0.01, prc:0
  scheduled ev:0, cev:0, sampl:0
```

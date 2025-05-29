```
NLLSsolver.CostTrajectory
```

フィールドを持つ型

```julia
    costs::Vector{Float64}
    times_ns::Vector{UInt64}
    trajectory::Vector{Vector{Float64}}
```

イテレーションごとの最適化情報を保存するために使用できます。

---

```julia
    CostTrajectory()
```

空の `CostTrajectory` 構造体を構築し、[`storecostscallback`](@ref) と一緒に使用する準備が整いました。

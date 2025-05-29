```
projected_energy(df::DataFrame; skip=0, hproj=:hproj, vproj=:vproj, kwargs...)
projected_energy(sim::PMCSimulation; kwargs...)
-> r::RatioBlockingResult
```

投影エネルギー推定量を計算します

$$
E_\mathrm{p} = \frac{\sum_n  \mathbf{v}⋅Ĥ\mathbf{c}^{(n)}}
        {\sum_m \mathbf{v}⋅\mathbf{c}^{(m)}} ,
$$

ここで、時系列 `df.hproj ==` $\mathbf{v}⋅Ĥ\mathbf{c}^{(n)}$ および `df.vproj ==` $\mathbf{v}⋅\mathbf{c}^{(m)}$ は `df` から取得され、最初の `skip` エントリをスキップします（これを設定するには `post_step_strategy =`[`ProjectedEnergy`](@ref Main.ProjectedEnergy)`(...)` を使用して [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem) に設定します）。 `projected_energy` は `h=0` の [`mixed_estimator`](@ref) と同等です。

キーワード引数 `hproj` と `vproj` は、関連する列の名前を変更するために使用できます。他の `kwargs` は [`ratio_of_means`](@ref) に渡されます。返されるのは [`RatioBlockingResult`](@ref) です。

結果の処理については、[`NamedTuple`](@ref)、[`val_and_errs`](@ref)、[`val`](@ref)、[`errs`](@ref) を参照してください。

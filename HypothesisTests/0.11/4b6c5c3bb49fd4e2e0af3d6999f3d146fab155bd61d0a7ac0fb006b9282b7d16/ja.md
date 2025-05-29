```
MannWhitneyUTest(x::AbstractVector{<:Real}, y::AbstractVector{<:Real})
```

`x`と`y`が同じ母集団からの観測値であるという帰無仮説に基づいて、`x`から引いた観測値が`y`から引いた観測値より大きい確率が、`y`から引いた観測値が`x`から引いた観測値より大きい確率と等しいという仮定の下で、マン・ホイットニーU検定を実施します。これらの確率が等しくないという対立仮説に対して検定を行います。

マン・ホイットニーU検定は、ウィルコクソン順位和検定としても知られています。

順位が tied でなく、サンプル数が≤50の場合、または順位が tied でサンプル数が≤10の場合、`MannWhitneyUTest`は正確なマン・ホイットニーU検定を実施します。それ以外の場合、`MannWhitneyUTest`は近似的なマン・ホイットニーU検定を実施します。動作は、[`ExactMannWhitneyUTest`](@ref) または [`ApproximateMannWhitneyUTest`](@ref) を直接使用することでさらに制御できます。

実装: [`pvalue`](@ref) ```

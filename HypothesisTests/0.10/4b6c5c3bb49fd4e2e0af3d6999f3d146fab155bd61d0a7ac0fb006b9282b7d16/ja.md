```
MannWhitneyUTest(x::AbstractVector{<:Real}, y::AbstractVector{<:Real})
```

`x`と`y`の同じ母集団から抽出された観察値のうち、`x`から抽出された観察値が`y`から抽出された観察値より大きい確率が、`y`から抽出された観察値が`x`から抽出された観察値より大きい確率と等しいという帰無仮説に対して、これらの確率が等しくないという対立仮説を検定するマン・ホイットニーU検定を実行します。

マン・ホイットニーU検定は、ウィルコクソン順位和検定として知られることもあります。

順位が tied でなく、サンプル数が≤50の場合、または順位が tied でありサンプル数が≤10の場合、`MannWhitneyUTest`は正確なマン・ホイットニーU検定を実行します。それ以外の場合、`MannWhitneyUTest`は近似的なマン・ホイットニーU検定を実行します。動作は、[`ExactMannWhitneyUTest`](@ref) または [`ApproximateMannWhitneyUTest`](@ref) を直接使用することでさらに制御できます。

実装: [`pvalue`](@ref) ```

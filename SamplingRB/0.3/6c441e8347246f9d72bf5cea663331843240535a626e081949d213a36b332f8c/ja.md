```
cvar_rbp(B::Vector{Float64}, alpha::Float64, rel_losses::Array{Float64,2}; tol::Float64=1e-6, maxiters::Int=1000)
```

リスク嗜好が `B` にあり、相対損失の行列 `rel_losses` に基づいて、CV@R-`alpha` リスクバジェットポートフォリオを構築するための資産の投資ウェイトを計算します。この行列のサイズは (|B|, nsamples) であり、各列は相対損失のサンプルに対応し、各行は特定の資産に対応します。

アルゴリズムは、（絶対的および相対的な）許容誤差 `tol` 内で証明可能な最適性ギャップに達するか、`maxiters` 回の反復後に収束に失敗した場合に停止します。

返り値は (failed, w) :: Bool, Vector{Float64} です。

アルゴリズムの詳細については、`cutting_planes_cvar` を参照してください。

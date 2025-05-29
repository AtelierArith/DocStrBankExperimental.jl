```
ParameterProfiles(DM::AbstractDataModel, Confnum::Real=2, Inds::AbstractVector{<:Int}=1:pdim(DM); adaptive::Bool=true, N::Int=31, plot::Bool=isloaded(:Plots), SaveTrajectories::Bool=true, IsCost::Bool=true, parallel::Bool=true, dof::Int=DOF(DM), kwargs...)
```

パラメータ $θ \in \mathcal{M}$ のコンポーネント `Inds` に対するプロファイル尤度を、与えられた `Domain` 上で計算します。n 番目の行列の最初の列は n 番目のコンポーネントの値を指定し、2 番目の列は n 番目のコンポーネントが最初の列の関連値に固定されている条件下での最適適合構成の関連信頼レベルを指定します。`Confnum` は、可能であればプロファイルを計算する信頼レベルを指定し、`Confnum=2` は 2σ に対応し、すなわち約 95.4% です。プロファイルオブジェクト `P` が与えられた場合、単一のプロファイルには `P[i]` を介してアクセスできます。

kwarg `IsCost=true` を使用すると、尤度値から関連する信頼レベルへの変換をスキップでき、プロファイルの 2 番目の列には `2(LogLikeMLE(DM) - loglikelihood(DM, θ))` が返されます。プロファイルに沿った再最適化中に追跡された軌跡は、`SaveTrajectories=true` を介して保存できます。`adaptive=false` の場合、ドメインのサイズは逆フィッシャー計量から推定され、プロファイルは固定ステップサイズグリッド上で評価されます。さらに、最適化に `kwargs` を渡すことができます。

# 拡張ヘルプ

結果の視覚化のために、複数の方法が利用可能です。例えば、[`PlotProfileTrajectories`](@ref) や [`PlotRelativeParameterTrajectories`](@ref) を参照してください。

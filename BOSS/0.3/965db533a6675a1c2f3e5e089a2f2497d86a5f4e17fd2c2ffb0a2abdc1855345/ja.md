ポテンシャルな次の評価点の「質」を説明する獲得関数を指定します。このタイプを継承してカスタム獲得関数を定義します。

例: `struct CustomAcq <: AcquisitionFunction ... end`

すべての獲得関数は*次のことを実装する必要があります*: `(acquisition::CustomAcq)(problem::BossProblem, options::BossOptions)`

このメソッドは、次の評価関数を選択するために最大化される関数 `acq(x::AbstractVector{<:Real}) = val::Real` を返す必要があります。

詳細については、[`ExpectedImprovement`](@ref)を参照してください。

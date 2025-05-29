```
VariancePropagation(DM::AbstractDataModel, mle::AbstractVector, Confnum::Real; dof::Int=DOF(DM), kwargs...)
VariancePropagation(DM::AbstractDataModel, mle::AbstractVector, C::AbstractMatrix=quantile(Chisq(length(mle)), ConfVol(1)) * Symmetric(pinv(FisherMetric(DM, mle))); kwargs...)
```

パラメータ共分散の前方伝播を残差に対して計算します。出力は、残差に関連する分散のコレスキー分解（すなわち平方根）を構成します。行列 `C` は、所望の信頼レベルに応じて適切にスケーリングされたパラメータ共分散行列 `Σ` に対応します。

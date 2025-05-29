```
bootstrap_with_candidates(::Type{GeometricGO}, rng::Random.AbstractRNG,Y::AbstractMatrix{T1}, X::AbstractMatrix{T2},Xpred::AbstractMatrix{T2}, nboot::Int=500; candidates_threshold::Real=0.05, genomic_control::Bool=true, tw_threshold::Real=0.001) where {T1<:Real,T2<:Real}
```

ブートストラップアプローチを使用してジオメトリックゲノムオフセットを計算します。各ブートストラップ反復ごとに、モデルは`Y`の列のランダムなサブセットを使用してフィッティングされます。トレイシー・ウィドムテストを使用して潜在因子の数を推定します。Fテストを使用して、適応的な遺伝子座を選択します。選択された遺伝子座に対してゲノムオフセットが計算されます。

# 引数

  * `rng::Random.AbstractRNG`: 擬似乱数生成器。指定されていない場合、グローバルRNGが使用されます。
  * `Y::AbstractMatrix{T1}`: 個体の遺伝子型またはアレル頻度を持つNxL行列。
  * `X::AbstractMatrix{T2}`: 環境データを持つNxP行列。
  * `Xpred::AbstractMatrix{T2}`: 予測された/変更された環境行列を持つNxP行列。
  * `nboot::Int=500`: ブートストラップ反復の数。
  * オプションの引数:

      * `candidates_threshold::Real=0.05`: Fテストの閾値。許容的である方が良い。
      * `genomic_control::Bool=true`: Fテストにゲノムコントロールを適用する。
      * `tw_threshold::Real=0.001`: トレイシー・ウィドムテストの閾値。保守的である方が良い（潜在因子の数はしばしば過保守的であるため）。
      * λ::Real=1e-5: LFMMの正則化パラメータ。

# 戻り値

  * ゲノムオフセット値を持つサイズNxNbootの行列。候補となる遺伝子座が見つからない場合、その行はゼロで埋められます。

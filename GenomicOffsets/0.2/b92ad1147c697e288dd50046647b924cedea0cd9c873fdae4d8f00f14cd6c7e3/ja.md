```
bootstrap_with_candidates(::Type{RDAGO}, rng::Random.AbstractRNG, Y::AbstractMatrix{T1}, X::AbstractMatrix{T2}, Xpred::AbstractMatrix{T2}, nboot::Int=500; candidates_threshold::Real=0.05, genomic_control::Bool=true, tw_threshold::Real=0.001) where {T1<:Real, T2<:Real}
```

ブートストラップアプローチを使用してRDAゲノムオフセットを計算します。各ブートストラップ反復ごとに、モデルは`Y`の列のランダムなサブセットを使用してフィッティングされます。トレーシー・ウィドム検定を使用して潜在因子の数を推定します。F検定を使用して、適応的なローカスを選択します。選択されたローカスに対してゲノムオフセットが計算されます。

# 引数

  * `rng::Random.AbstractRNG`: ランダム数生成器。指定されていない場合、グローバルRNGが使用されます。
  * `Y::AbstractMatrix{T1}`: 個体の遺伝子型またはアレル頻度を持つNxL行列。
  * `X::AbstractMatrix{T2}`: 環境データを持つNxP行列。
  * `Xpred::AbstractMatrix{T2}`: 予測された/変更された環境行列を持つNxP行列。
  * `nboot::Int=500`: ブートストラップ反復の数。
  * オプションの引数:

      * `candidates_threshold::Real=0.05`: F検定の閾値。許容的である方が良い。
      * `genomic_control::Bool=true`: F検定にゲノムコントロールを適用する。
      * `tw_threshold::Real=0.001`: トレーシー・ウィドム検定の閾値。保守的である方が良い（潜在因子の数はしばしば過保守的であるため）。
      * `pratio::Float64=0.99`: 主成分サブスペースで保持される分散の比率。
      * `weighted::Bool=false`: 真の場合、投影空間でのユークリッド距離は各軸の固有値に基づいて重み付けされる。
      * λ::Real=1e-5: LFMMの正則化パラメータ。

# 戻り値

  * ゲノムオフセット値を持つNxNbootのサイズの行列。候補ローカスが見つからない場合、行はゼロで埋められます。

```

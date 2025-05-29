ライブラリ構築パラメータを含むラッパー

  * `knockdown_dist`: ガイドのノックダウン効率の分布
  * `knockdown_probs`
  * `max_phenotype_dists`: 選択される確率にマッピングされた最大表現型カテゴリと、選択された場合に引き出すための分布。

    ## 例

    基本的なレイアウトは、クラス名を選択する確率のタプルにマッピングされた `Dict` であり、その後、このクラスからランダムな表現型を引き出すための [`Distributions.Sampleable`](https://juliastats.github.io/Distributions.jl/latest/types.html#Sampleable-1) です。すべてのクラスの確率は合計して1になるべきです。

    ```julia
    max_phenotype_dists = Dict{Symbol, Tuple{Float64, Sampleable}}(
        :inactive => (0.60, Delta(0.0)),
        :negcontrol => (0.1, Delta(0.0)),
        :increasing => (0.3, truncated(Normal(0.1, 0.1), 0.025, 1)),
    );
    Library(max_phenotype_dists, CRISPRi());
    ```

    例えば、ここでは「遺伝子」の3つの異なるクラスを作成しています：最初のグループは :inactive で、すなわち表現型がないため、[`Crispulator.Delta`](@ref) を使用してその表現型を0.0に設定します。これらはすべての遺伝子の60%を占めます。2番目のグループは負のコントロール :negcontrol （唯一の必須グループ）で、遺伝子の10%を占め、効果はありません。最後のグループは :increasing で、すべての遺伝子の30%を占め、Normal(μ=0.1, σ=0.1) 分布で0.025と1の間に制限されています。
  * `phenotype_probs`
  * `kd_phenotype_relationships`: ノックダウン-表現型関係が選択される確率とそれぞれの [`Crispulator.KDPhenotypeRelationship`](@ref) にマッピングされています。
  * `relationship_probs`
  * `cas9_behavior`: このライブラリが [`Crispulator.CRISPRi`](@ref) か [`Crispulator.CRISPRn`](@ref) か。

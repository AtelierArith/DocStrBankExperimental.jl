```
run_model_rh(case::AbstractCase, model::RecHorEnergyModel, optimizer; check_timeprofiles::Bool=true)
```

変数 `case` と `model` を取り、問題を再帰的ホライズン方式で最適化します。これは一連の最適化問題として行われます。

!!! warning "必要な入力"
    [`Case`](@extref EnergyModelsBase.Case) 型は柔軟ですが、特定の構造に従う必要があります。

      * `case` 型は、辞書フィールド `misc` に追加の入力として、[`AbstractHorizons`](@ref) 型に対応するエントリ `:horizons` を必要とします。
      * フィールド `elements` 内の個々の要素ベクターの順序は、コードの構造のために現時点では任意ではありません。次の順序を**必ず**使用してください：

        1. `Vector{<:EMB.Node}`
        2. `Vector{<:Link}`
        3. `Vector{<:Area}`
        4. `Vector{<:Transmission}`

        この構造を使用しない場合、モデルは実行されません。


`results` をモデル変数でインデックス付けされたデータフレームとして返します。

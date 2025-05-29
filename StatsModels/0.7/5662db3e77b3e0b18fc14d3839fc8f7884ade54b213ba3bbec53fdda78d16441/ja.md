```
ModelFrame(formula, data; model=StatisticalModel, contrasts=Dict())
```

`FormulaTerm`、スキーマ、データテーブル、およびモデルタイプをカプセル化するラッパーです。

このラッパーは、ラップされたデータフレームと同じ構造のデータをモデル行列（`FormulaTerm`）に変換するために必要なすべての情報と、そのフォーミュラ項がどのようにインスタンス化されたかに関する情報（スキーマとモデルタイプ）をカプセル化します。

モデルフレームを作成するには、まずデータの[`schema`](@ref)を抽出し（提供されたコントラストをヒントとして使用）、次にそのスキーマを[`apply_schema`](@ref)を使用して、提供されたモデルタイプのコンテキスト内でフォーミュラに適用します。

# コンストラクタ

```julia
ModelFrame(f::FormulaTerm, data; model::Type{M} = StatisticalModel, contrasts::Dict = Dict())
```

# フィールド

  * `f::FormulaTerm`: 左辺が*応答*、右辺が*予測子*であるフォーミュラ。
  * `schema::Any`: `f`を生成するために適用されたスキーマ。
  * `data::D`: モデリングされるデータテーブル。唯一の制約は、`data`がテーブルであること（`Tables.istable(data) == true`）。
  * `model::Type{M}`: このモデルフレームからフィットされるモデルのタイプ。

# 例

```julia
julia> df = (x = 1:4, y = 5:8)
julia> mf = ModelFrame(@formula(y ~ 1 + x), df)
```

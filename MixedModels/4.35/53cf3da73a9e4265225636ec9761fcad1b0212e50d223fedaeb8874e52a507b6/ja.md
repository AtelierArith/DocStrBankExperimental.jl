```
struct Grouping <: StatsModels.AbstractContrasts end
```

カテゴリ変数が対比ではなくグループ化のみに使用されることを示すプレースホルダー型です。 `CategoricalTerm`を作成する際に、対比行列の構築をスキップするため、大量のレベルに対して堅牢でありながら、レベルのベクトルを保持し、レベルからインデックスへのマッピング（`ContrastsMatrix`の`invindex`フィールド）を構築します。

`CategoricalTerm{Grouping}`に対して`modelcols`を呼び出すことはエラーです。

# 例

```julia
julia> schema((; grp = string.(1:100_000)))
# out-of-memory error

julia> schema((; grp = string.(1:100_000)), Dict(:grp => Grouping()))
```

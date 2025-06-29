```
smote([rng=default_rng()], data::AbstractVecOrMat, n::Int; k::Union{Nothing,Int}=nothing)
smote([rng=default_rng()], data, n::Int; k::Union{Nothing,Int}=nothing)
```

合成少数オーバーサンプリング技術（SMOTE）（Chawla et al., [2002](https://doi.org/10.1613/jair.953)）によって得られたサンプルを返します。

  * `data`: 行列またはテーブルインターフェースを満たすデータ。行列の場合、各列はポイントを示し、テーブルの場合、各行はポイントを示します。
  * `n`: 作成すべき合成ポイントの数。
  * `k`: 各ポイントに対して考慮すべき最近傍の数。

各少数クラスに対して、アルゴリズムは`k`最近傍の1つの間の線に沿って合成ポイントを作成します。線に沿ったポイントの位置はランダムに選ばれます。

実装は論文の擬似コードに基づいていますが、論文には奇妙なAPI（特に`N`）があり、実装はインデックスロジックで満ちています。本質は擬似コードよりもはるかにシンプルです：`n`個の新しいポイントを見つけるために、少数グループから各`n`のためにランダムなポイント`p`を取り、各`p`について最近傍への線に沿ったランダムなポイントを取ります。

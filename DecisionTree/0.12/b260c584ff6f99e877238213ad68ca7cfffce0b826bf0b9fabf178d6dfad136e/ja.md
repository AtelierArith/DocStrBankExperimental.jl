```
impurity_importance(tree; normalize::Bool = false)
impurity_importance(forest)
impurity_importance(adaboost, coeffs)
```

`平均不純物減少 (MDI)` によって計算された特徴の重要性のベクトルを返します。

特徴の重要性は次のように計算されます：

  * 単一の木：各特徴について、その特徴に基づくすべての分割の不純物減少の合計を、分割ごとの不純物減少（ノードの不純物から子ノードの不純物の合計を引いたもの）で割ったものが関連する重要性です。`normalize` が true の場合、特徴の重要性は特徴の重要性の合計で正規化されます。

より明示的には、ノード i の不純物減少は次のようになります：

```
Δimpurityᵢ = nᵢ × lossᵢ - nₗ × lossₗ - nᵣ × lossᵣ
```

ここで n は観測の数、loss はエントロピー、ジニ指数、または他の不純物の測定値、インデックス i はノード i の量を示し、インデックス l は左子ノードの量、インデックス r は右子ノードの量を示します。

  * 森：特定の特徴の重要性は、その特徴に対する**正規化された**木の重要性の森林内の木の平均です。
  * AdaBoost モデル：特徴の重要性は `split_importance` と同じです。

森林とアダブーストモデルの場合、特徴の重要性は木の平均を取る前に正規化されるため、キーワード引数 `normalize` は無意味です。正規化するかどうかは議論の余地がありますが、現在の実装は `scikitlearn` の RandomForestClassifier、RandomForestRegressor、および AdaBoostClassifier と同じであり、G. Louppe の「Understanding Random Forests: From Theory to Practice」、PhD 論文、リエージュ大学、2014年に記載されている特徴の重要性とは異なります。詳細な議論についてはこの [PR](https://github.com/scikit-learn/scikit-learn/issues/19972) を参照してください。

`impurity_importance` が木を構築する際に false に設定されていた場合、この関数は空のベクトルを返します。

警告：重要性は MDI がバイアスのある方法であるため、誤解を招く可能性があります。詳細な議論については [Beware Default Random Forest Importances](https://explained.ai/rf-importance/index.html) を参照してください。

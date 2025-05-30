```
split_importance(tree; normalize::Bool = false)
split_importance(forest)
split_importance(adaboost, coeffs)
```

特徴が分割に使用された回数に基づいて特徴の重要度のベクトルを返します。

特徴の重要度は次のように計算されます：

  * 単一の木：各特徴に対して、関連する重要度はその特徴に基づく分割の数です。
  * 森：特定の特徴の重要度は、その特徴に対する**正規化された**木の重要度の森内の木の平均です。
  * AdaBoostモデル：各特徴の重要度は、各スタンプに基づく分割の平均数であり、推定器の重み（`coeffs`）で重み付けされます。

森とAdaBoostモデルの場合、特徴の重要度は木の平均を取る前に正規化されるため、キーワード引数`normalize`は無用です。

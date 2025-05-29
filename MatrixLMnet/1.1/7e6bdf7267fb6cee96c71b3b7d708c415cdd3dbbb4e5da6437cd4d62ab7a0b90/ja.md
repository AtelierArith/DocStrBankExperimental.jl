```
mlmnet_cv_summary(MLMNet_cv::Mlmnet_cv)
```

交差検証の結果を要約し、次の内容を含むテーブルを返します：

  * 使用されたラムダ
  * 各ラムダのフォールド間の平均MSE
  * 各ラムダのフォールド間のゼロ相互作用係数の平均割合

# 引数

  * MLMNet*cv = MLMNet*cvオブジェクト

# 値

各ラムダのフォールド間の平均MSEとゼロ相互作用の割合を要約したDataFrame。

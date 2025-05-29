```
lambda_min(MLMNet_cv::Mlmnet_cv)
```

最小平均テストMSEに対応するラムダの要約情報を返します。これは、フォールド間での標準誤差が1つ大きいMSEも含まれます。

# 引数

  * MLMNet*cv = MLMNet*cvオブジェクト

# 値

フォールド間での最小平均テストMSEに対応するラムダとアルファに制限されたmlmnet*cv*summaryからのDataFrame。

```
mlmnet_bic_summary(MLMNet_bic::Mlmnet_bic)
```

BIC検証の結果を要約し、次の内容を含むテーブルを返します：

  * 使用されたラムダ
  * 各ラムダのフォールド間のMSE
  * 各ラムダとアルファのペアにおけるゼロ相互作用係数の割合

# 引数

  * MLMNet*bic = Mlmnet*bicオブジェクト

# 値

BIC、MSE、各ラムダとアルファのペアにおけるゼロ相互作用の割合を要約したDataFrame。

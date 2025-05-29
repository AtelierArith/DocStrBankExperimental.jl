```
WSVarLmmModel
```

被験者内分散線形混合モデルで、`WSVarLmmObs`のベクトルをデータ、モデルパラメータ、および作業配列として含みます。

```
WSVarLmmModel(obsvec; obswts, meannames, renames, wsvarnames)
```

# 位置引数

  * `obsvec`: WSVarLmmObsのベクトル

# キーワード引数

  * `obswts`: 観察重みの被験者レベルの重みベクトル、`obsvec`オブジェクトの長さ。
  * `meannames`: 平均固定効果共変量の名前
  * `renames`: ランダム位置効果共変量の名前
  * `wsvarnames`: ws分散固定効果共変量の名前

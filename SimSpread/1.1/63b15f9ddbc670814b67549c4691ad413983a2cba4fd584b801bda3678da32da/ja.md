```
clean!(yhat::NamedArray, A::NamedArray, y::NamedArray)
```

フラグ、インプレースで、クロスバリデーション分割からの誤った予測。

# 引数

  * `yhat::NamedArray`: 予測されたソース-ターゲット二部隣接行列
  * `A::NamedArray`: 初期リソースソース-ターゲットリソース隣接行列
  * `y::NamedArray`: グラウンドトゥルースソース-ターゲット二部隣接行列

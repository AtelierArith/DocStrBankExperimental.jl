```
function local_search_CNN(start, cnn_jump; epsilon=0.01, max_iter=10, show_path=false, logging=false, tolerance=0.01)
```

与えられた畳み込みニューラルネットワークのJuMP定式化に対してリラクシングウォーク局所探索を実行します。詳細については、Tong et al. (2024)を参照してください。

# パラメータ

  * `start`: 探索の開始点（画像空間の座標）
  * `cnn_jump`: CNN定式化を含む`JuMP`モデル

# オプションのパラメータ

  * `epsilon`: 線形領域から出る際のステップサイズを制御します
  * `max_iter`: 最大探索ステップ数
  * `show_path`: 最適解に加えて局所探索によって取られた経路を返します
  * `logging`: コンソールに進捗情報を印刷します
  * `tolerance`: 探索を続けるために各ステップで必要な最小相対改善

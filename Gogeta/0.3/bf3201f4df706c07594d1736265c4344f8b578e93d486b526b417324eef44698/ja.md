```
function local_search(start, jump_model, U_in, L_in; max_iter=100, epsilon=0.01, show_path=false, silent=true, tolerance=0.001)
```

与えられたニューラルネットワークのJuMP定式化に対してリラクシングウォーク局所探索を実行します。詳細については、Tong et al. (2024)を参照してください。

# パラメータ

  * `start`: 探索の開始点（空間内の座標）
  * `jump_model`: NN定式化を含む`JuMP`モデル
  * `U_in`: ドメインの上限
  * `L_in`: ドメインの下限

# オプションのパラメータ

  * `epsilon`: 線形領域から出る際のステップサイズを制御します
  * `show_path`: 最適解に加えて局所探索によって取られた経路を返します
  * `silent`: 進行状況の情報をコンソールに印刷します
  * `tolerance`: 探索を続けるために各ステップで必要な最小相対改善

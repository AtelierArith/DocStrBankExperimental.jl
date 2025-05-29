```
solve(prob::DirectTimeProblem, alg; progress = true)
```

直接時間積分ソルバー

**入力**

  * `prob`: DirectTimeProblem 構造体
  * `alg`: 数値積分アルゴリズム

      * `CentralDiff()`: 中央差分
      * `RK4()`: 四次のルンゲ・クッタ法
      * `Newmark()`: ニューマーク法
      * `HHT()`: ヒルバー・ヒューズ・テイラー法
      * `WBZ()`: ウッド・ボサック・ジエンキェウィッチ法
      * `GeneralizedAlpha()`: 一般化α（デフォルト）
      * `MidPoint()`: 中点法
  * `progress`: 進捗バーを表示

**出力**

  * `sol`: 指定された時間点でのシステムの応答を含む解の構造体

      * `u`: 変位
      * `du`: 速度
      * `ddu`: 加速度

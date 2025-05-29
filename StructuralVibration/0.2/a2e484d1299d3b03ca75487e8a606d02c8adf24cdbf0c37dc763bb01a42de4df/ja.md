```
solve(prob::StateTimeSpaceProblem, alg = RK4(); progress = true)
```

状態空間モデルを使用して連続時間問題を解決します

**入力**

  * `prob`: 連続時間問題
  * `alg`: 時間積分アルゴリズム
  * `progress`: 進行状況バーを表示する (デフォルト = true)

**出力**

  * `StateSpaceSolution`: 状態空間モデルの解

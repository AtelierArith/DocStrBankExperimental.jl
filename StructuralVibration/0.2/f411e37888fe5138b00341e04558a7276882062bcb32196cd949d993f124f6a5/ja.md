```
solve(prob::StateSpaceTimeProblem, method = :zoh; progress = true)
```

状態空間モデルを使用して離散時間問題を解決します

**入力**

  * `prob`: 離散時間問題
  * `method`: 離散化手法

      * `:zoh`: ゼロオーダーホールド法
      * `:foh`: 一次オーダーホールド法
      * `:blh`: バンド制限ホールド法
      * `:rk4`: ルンゲクッタ4次法
  * `progress`: 進行状況バーを表示する (デフォルト = true)

**出力**

  * `StateSpaceSolution`: 状態空間モデルの解

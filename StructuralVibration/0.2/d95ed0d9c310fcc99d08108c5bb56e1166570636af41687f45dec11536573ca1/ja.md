```
solve(prob::StateSpaceFreqProblem; type = :dis, progress = true)
solve(prob::StateSpaceFreqProblem; type = :dis, progress = true)
```

周波数応答を直接法またはモーダル法で計算します

**入力**

  * `prob`: 問題データを含む構造体
  * `type::Symbol`: 計算するFRFのタイプ

      * `:dis`: 変位
      * `:vel`: 速度
      * `:acc`: 加速度
  * `progress`: 進行状況バーを表示

**出力** `sol`: 問題の解     * `u`: 応答スペクトル行列

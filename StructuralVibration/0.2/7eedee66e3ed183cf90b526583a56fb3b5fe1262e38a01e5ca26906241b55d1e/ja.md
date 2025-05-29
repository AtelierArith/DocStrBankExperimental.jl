```
solve(prob::DirectFreqProblem; type = :dis, progress = true)
solve(prob::ModalFreqProblem; type = :dis, progress = true)
```

直接またはモーダルアプローチによる周波数応答を計算します

**入力**

  * `prob`: 問題データを含む構造体
  * `type`: 計算する応答のタイプ

      * `:dis`: 変位（デフォルト）
      * `:vel`: 速度
      * `:acc`: 加速度
  * `progress`: 進行状況バーを表示する（デフォルト = true）

**出力**

  * `sol`: 問題の解

      * `u`: 応答スペクトル行列

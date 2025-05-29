```
gradient(f::Vector{Real}, t; method = :cubic)
gradient(f::Matrix{Real}, t; method = :cubic, dims = 1)
```

関数 `f` の点 `t` での勾配を計算します。

**入力**

  * `f`: 関数値
  * `t`: 勾配を評価する点
  * `method`: 補間方法

      * `:linear`: 線形補間
      * `:cubic`: 三次スプライン補間（デフォルト）
  * `dims`: 勾配を計算する次元

      * `1`: 行（デフォルト）
      * `2`: 列

**出力**

  * `df`: 点 `t` でのベクトル `f` の勾配

**注意**

`method` が `:cubic` の場合、`t` は `AbstractRange` でなければなりません。

```
solve(prob::FreeModalTimeProblem)
```

モーダルアプローチを使用して、多自由度（Mdof）システムの自由応答を計算します。

**入力**

  * `prob`: Mdof 問題のパラメータを含む構造体

**出力**

  * `sol`: 指定された時間点でのシステムの応答を含む ModalTimeSolution 構造体

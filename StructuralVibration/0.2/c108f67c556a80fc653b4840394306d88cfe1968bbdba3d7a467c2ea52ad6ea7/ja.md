```
solve(prob::ForcedModalTimeProblem)
```

任意の励起による多自由度 (Mdof) システムの強制応答をモーダルアプローチを使用して計算します。

**入力**

  * `prob`: Mdof 問題のパラメータを含む構造体
  * `method`: デュハメルの積分を計算する方法

      * `:filt`: インパルス応答の Z 変換を使用したフィルタリング (デフォルト)
      * `:interp`: 補間 + ガウス求積
      * `:conv`: 畳み込み

**出力**

  * `sol`: 指定された時点でのシステムの応答を含む ModalTimeSolution 構造体

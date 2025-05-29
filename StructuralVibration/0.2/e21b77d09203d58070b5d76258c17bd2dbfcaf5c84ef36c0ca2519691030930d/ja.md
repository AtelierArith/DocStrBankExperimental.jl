```
solve(prob::SdofFreeTimeProblem)
```

単自由度(Sdof)システムの自由応答を計算します。

**入力**

  * `prob`: Sdof問題のパラメータを含む構造体

**出力**

  * `sol`: 指定された時間点でのシステムの応答

      * `u`: 変位解
      * `du`: 速度解
      * `ddu`: 加速度解

```
RAD(x, τ=1, doAbs=true)
```

再スケーリングされた自己密度を計算します。これは、ノイズ強度の不確実性に対して鈍感な臨界点への距離を推測するための指標です。可変で未知の測定ノイズを伴うホップ分岐に関する実験にキャリブレーションされています。

入力:     x:      入力時系列（ベクトル）。     doAbs:  時系列を0で中心にしてから絶対値を取るかどうか（論理フラグ）     τ:      タイムステップの単位での埋め込みおよび差分遅延（整数）、または :τ

出力:     f:      RAD特徴値 ```

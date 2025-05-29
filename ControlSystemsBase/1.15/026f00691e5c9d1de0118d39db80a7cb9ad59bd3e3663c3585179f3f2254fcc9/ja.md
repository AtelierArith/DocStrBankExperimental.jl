```
are(::Continuous, A, B, Q, R)
```

連続時間代数リカッティ方程式の解 'X' を計算します。これは A'X + XA - (XB)R^-1(B'X) + Q = 0 と定義され、R は非特異です。

LQR 問題では、`Q` は状態ペナルティ $x'Qx$ に関連し、`R` は制御ペナルティ $u'Ru$ に関連します。詳細については [`lqr`](@ref) を参照してください。

`MatrixEquations.arec` を使用します。キーワード引数については、`ControlSystemsBase.MatrixEquations.arec` のドキュメントを参照してください。入力引数の順序が異なることに注意してください。 ```

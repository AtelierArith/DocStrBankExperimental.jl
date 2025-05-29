```
are(::Discrete, A, B, Q, R; kwargs...)
```

離散時間代数リカッティ方程式の解である `X` を計算します。これは次のように定義されます： A'XA - X - (A'XB)(B'XB + R)^-1(B'XA) + Q = 0、ここで Q>=0 および R>0 です。

LQR 問題では、`Q` は状態ペナルティ $x'Qx$ に関連し、`R` は制御ペナルティ $u'Ru$ に関連します。詳細については [`lqr`](@ref) を参照してください。

`MatrixEquations.ared` を使用します。キーワード引数については、`ControlSystemsBase.MatrixEquations.ared` のドキュメントを参照してください。入力引数の順序が異なることに注意してください。 ```

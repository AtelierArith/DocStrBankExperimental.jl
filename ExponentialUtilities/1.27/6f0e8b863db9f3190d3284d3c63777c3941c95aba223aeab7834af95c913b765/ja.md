```
struct ExpMethodGeneric{T}
ExpMethodGeneric()=ExpMethodGeneric{Val{13}}();
```

任意の exp 引数 `x` に対するメソッド `ExpMethodHigham2005` の一般的な指数実装。ここで、関数 `LinearAlgebra.opnorm`、`+`、`*`、`^`、および `/`（UniformScaling オブジェクトとの加算を含む）が定義されています。型 `T` は、コンパイル時に Pade 近似に使用される項の数を調整するために使用されます。

アルゴリズムの詳細については、2005 年の Higham, Nicholas J. による「行列指数のためのスケーリングと二乗法の再考」を参照してください。

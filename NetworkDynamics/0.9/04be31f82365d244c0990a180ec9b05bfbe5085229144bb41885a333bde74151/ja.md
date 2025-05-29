```
init_residual(cf::T; t=NaN, recalc=false)
```

指定されたコンポーネントモデルに対して、`default`および`init` [Metadata](@ref) を介して提供された値に対する残差 |du| を計算します。

recalc=false の場合、実際の初期化プロセスで決定された残差を返します。

関連情報として [`initialize_component!`](@ref) も参照してください。

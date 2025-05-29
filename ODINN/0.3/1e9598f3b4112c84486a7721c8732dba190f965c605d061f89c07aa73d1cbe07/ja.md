```
ContinuousAdjoint{
    F <: AbstractFloat,
    I <: Integer,
    VJP <: AbstractVJPMethod
    } <: AbstractAdjointMethod
```

SIA2Dの連続随伴とODEスキームにおけるバックワードの手動実装。

# フィールド

  * `VJP_method::VJP`: 随伴計算内でVJPを計算するために使用されるAbstractVJPMethodの型。
  * `solver::Any`: 随伴に使用されるソルバー。
  * `reltol::F`: 随伴のODEソルバーで使用される相対許容誤差。
  * `abstol::F`: 随伴のODEソルバーで使用される絶対許容誤差。
  * `n_quadrature::I`: 損失関数の数値積分のためにガウス求積で使用されるノードの数。

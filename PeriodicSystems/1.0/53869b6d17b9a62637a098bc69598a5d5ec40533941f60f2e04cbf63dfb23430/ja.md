```
PeriodicStateSpace(A::PM, B::PM, C::PM, D::PM) -> psys::PeriodicStateSpace{PM}
```

周期行列オブジェクトの4つの組から`PeriodicStateSpace`オブジェクトを構築します。

周期行列オブジェクト`A`、`B`、`C`、`D`は、連続時間形式の線形周期時変状態空間モデルの周期行列`A(t)`、`B(t)`、`C(t)`および`D(t)`を指定します。

```
 dx(t)/dt = A(t)x(t) + B(t)u(t) ,
 y(t)     = C(t)x(t) + D(t)u(t) ,
```

または離散時間形式では

```
 x(t+1)  = A(t)x(t) + B(t)u(t) ,
 y(t)    = C(t)x(t) + D(t)u(t) ,
```

ここで、`x(t)`、`u(t)`および`y(t)`はそれぞれシステム状態ベクトル、システム入力ベクトルおよびシステム出力ベクトルであり、`t`は連続または離散の時間変数です。システム行列は`A(t) = A(t+T₁)`、`B(t) = B(t+T₂)`、`C(t) = C(t+T₃)`、`D(t) = D(t+T₄)`を満たし、すなわち、周期`T₁`、`T₂`、`T₃`および`T₄`で周期的です。異なる周期は互いに整合性がなければならず（すなわち、その比率は分子と分母が最大で4桁の有理数でなければなりません）。すべての周期行列オブジェクトは同じ型`PM`を持たなければならず、ここで`PM`はサポートされている周期行列型の1つを表します。すなわち、`PeriodicMatrix`、`SwitchingPeriodicMatrix`、`PeriodicArray`、`SwitchingPeriodicArray`、`PeriodicFunctionMatrix`、`PeriodicSymbolicMatrix`、`HarmonicArray`、`FourierFunctionMatrix`、`PeriodicTimeSeriesMatrix`または`PeriodicSwitchingMatrix`です。

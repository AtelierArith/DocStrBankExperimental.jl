```
ps([PMT::Type,] A::PM1, B::PM2, C::PM3, D::PM4) -> psys::PeriodicStateSpace
```

周期的な行列オブジェクトの四重項から `PeriodicStateSpace` オブジェクトを構築します。

周期的な行列オブジェクト `A`、`B`、`C`、`D` は、連続時間形式の線形周期的時間変化状態空間モデルの周期的行列 `A(t)`、`B(t)`、`C(t)` および `D(t)` を指定します。

```
 dx(t)/dt = A(t)x(t) + B(t)u(t) ,
 y(t)     = C(t)x(t) + D(t)u(t) ,
```

または離散時間形式では

```
 x(t+1)  = A(t)x(t) + B(t)u(t) ,
 y(t)    = C(t)x(t) + D(t)u(t) ,
```

ここで `x(t)`、`u(t)` および `y(t)` はそれぞれシステム状態ベクトル、システム入力ベクトルおよびシステム出力ベクトルであり、`t` は連続または離散の時間変数です。システム行列は `A(t) = A(t+T₁)`、`B(t) = B(t+T₂)`、`C(t) = C(t+T₃)`、`D(t) = D(t+T₄)` を満たし、すなわち周期 `T₁`、`T₂`、`T₃` および `T₄` で周期的です。異なる周期は互いに整合性がなければなりません（すなわち、その比は最大4桁の有理数でなければなりません）。周期的な行列オブジェクト `A`、`B`、`C`、`D` はそれぞれ異なるタイプ `PM1`、`PM2`、`PM3`、`PM4` を持つことができ、連続時間システムの場合、`PM1`、`PM2`、`PM3`、`PM4` はサポートされている連続時間周期行列タイプのいずれかでなければなりません。すなわち、`PeriodicFunctionMatrix`、`PeriodicSymbolicMatrix`、`HarmonicArray`、`FourierFunctionMatrix` または `PeriodicTimeSeriesMatrix` です。一方、離散時間システムの場合、`PM1`、`PM2`、`PM3`、`PM4` はサポートされている離散時間周期行列タイプのいずれかでなければなりません。すなわち、`PeriodicMatrix` または `PeriodicArray` です。オブジェクト `A`、`B`、`C`、`D` のいずれも適切なサイズの実行列またはベクトルとして指定することもできます。

`PMT` が指定されていない場合、結果の `psys` は同じタイプ `PT` の周期行列を持ち、`PT` はすべての行列オブジェクトの共通タイプであるか、連続時間システムの場合は `PT = PeriodicFunctionMatrix`、離散時間システムの場合は `PT = PeriodicMatrix` です。`PMT` が指定されている場合、結果の `psys` は同じタイプ `PMT` の周期行列を持ちます。

他の便利なコンストラクタは次のように実装されています：

```
ps([PMT::Type,] A, B, C) -> psys::PeriodicStateSpace
```

四重項 `(A,B,C,0)` のための `PeriodicStateSpace` オブジェクトを構築します。

```
ps(D) -> psys::PeriodicStateSpace
```

四重項 `([],[],[],D)` のための `PeriodicStateSpace` オブジェクトを構築します。

```
ps([PMT::Type,] A, B, C, D, period) -> psys::PeriodicStateSpace
```

四重項 `(A,B,C,D)` のために希望する `period` を持つ `PeriodicStateSpace` オブジェクトを構築します。すべてのオブジェクト `A`、`B`、`C`、`D` は適切なサイズの実行列またはベクトルとして指定することもできます。

```
ps([PMT::Type,] A, B, C, period) -> psys::PeriodicStateSpace
```

四重項 `(A,B,C,0)` のために希望する `period` を持つ `PeriodicStateSpace` オブジェクトを構築します。すべてのオブジェクト `A`、`B`、`C` は適切なサイズの実行列またはベクトルとして指定することもできます。

```
ps(sys::DescriptorStateSpace, period) -> psys::PeriodicStateSpace
```

四重項 `(sys.A,sys.B,sys.C,sys.D)` のために希望する `period` を持つ `PeriodicStateSpace` オブジェクトを構築します（`sys.E = I` が仮定されます）。

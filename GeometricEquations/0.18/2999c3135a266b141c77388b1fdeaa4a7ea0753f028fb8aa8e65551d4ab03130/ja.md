`GeometricEquation{invType,parType,perType}` は、すべての方程式タイプが派生する抽象型です。

すべての方程式は、主状態変数の不変量、パラメータ、および周期性を定義するためのフィールドを持つ必要があります。これらのフィールドの型は、次の型パラメータに格納されています：

  * `invType <: OptionalInvariants`: 不変量の型
  * `parType <: OptionalParameters`: パラメータの型
  * `perType <: OptionalPeriodicity`: 周期性の型

`Optional*` 型はすべて、それぞれの `Null*` 型と `NamedTuple` または `AbstractArray` の和集合です。すなわち、

```julia
const OptionalInvariants = Union{NamedTuple, NullInvariants}
const OptionalParameters = Union{NamedTuple, NullParameters}
const OptionalPeriodicity = Union{AbstractArray, NullPeriodicity}
```

`Null*` 型は空の構造体であり、単にディスパッチと特性 `hasinvariants`、`hasparameters`、および `hasperiodicity` のために使用されます。

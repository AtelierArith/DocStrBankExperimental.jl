```
UnitFactor <: AbstractUnit
```

名前付き単位の型 [`BaseUnit`](@ref)、それを修正するタイプの接頭辞 [`UnitPrefix`](@ref)、およびペアがどの累乗に上げられるかを示す指数から構成される複合単位です。

# フィールド

  * `unitPrefix::UnitPrefix`
  * `baseUnit::BaseUnit`
  * `exponent::Real`

# コンストラクタ

```
UnitFactor(unitPrefix::UnitPrefix, baseUnit::BaseUnit, exponent::Real)
UnitFactor(baseUnit::BaseUnit, exponent::Real)
UnitFactor(unitPrefix::UnitPrefix, baseUnit::BaseUnit)
UnitFactor(baseUnit::BaseUnit)
UnitFactor()
```

コンストラクタ呼び出しから3つのフィールドのいずれかが省略された場合、そのフィールドは対応するデフォルト値を使用して初期化されます：

  * `unitPrefix = unitPrefix=Alicorn.emptyUnitPrefix`
  * `baseUnit = Alicorn.unitlessBaseUnit`
  * `exponent = 1`

# 例外を発生させる

  * `Core.DomainError`: 指数フィールドに無限大の数を初期化しようとした場合

# 備考

コンストラクタは、可能であれば指数を `Int` に変換します。 `baseUnit=Alicorn.unitlessBaseUnit` の場合、接頭辞は常に `unitPrefix=Alicorn.emptyUnitPrefix` に設定され、指数は `exponent=1` に設定されます。

# 例

1. 単位 $\mathrm{km}^2$（平方キロメートル）は、次のように型コンストラクタメソッドを使用して構築できる `UnitFactor` で表すことができます：

    ```jldoctest  julia> ucat = UnitCatalogue();

    julia> UnitFactor(ucat.kilo, ucat.meter, 2)  UnitFactor km^2  ```
2. あるいは、$\mathrm{km}^2$ は算術的に構築することもできます：

    ```jldoctest  julia> ucat = UnitCatalogue();

    julia> (ucat.kilo * ucat.meter)^2  UnitFactor km^2  ```

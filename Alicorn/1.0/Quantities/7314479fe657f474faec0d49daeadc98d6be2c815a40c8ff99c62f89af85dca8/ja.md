```
InternalUnits
```

SIシステムの7つの基本物理次元に関して測定される単位の選択を表す7つの`SimpleQuantity`オブジェクトのセットです。

# フィールド

  * `mass::SimpleQuantity`: 質量の単位
  * `length::SimpleQuantity`: 長さの単位
  * `time::SimpleQuantity`: 時間の単位
  * `current::SimpleQuantity`: 電流の単位
  * `temperature::SimpleQuantity`: 温度の単位
  * `amount::SimpleQuantity`: 量の単位
  * `luminousIntensity::SimpleQuantity`: 明るさの単位

# コンストラクタ

```
InternalUnits(::SimpleQuantity, ::SimpleQuantity, ::SimpleQuantity, ::SimpleQuantity, ::SimpleQuantity, ::SimpleQuantity, ::SimpleQuantity)
InternalUnits(; mass = 1*kilogram, length = 1*meter, time = 1*second, current = 1*ampere,temperature = 1*kelvin, amount = 1*mol, luminousIntensity = 1*candela)

# 例外を発生させる
- `Core.DomainError`: 値がゼロ、無限大、または実数でない量でフィールドを初期化しようとした場合
- `Exceptions.DimensionMismatchError`: フィールドが表す物理次元と一致しない次元の量でフィールドを初期化しようとした場合

# 例
次の`InternalUnits`は長さを``3 cm``の単位で測定し、他のすべての次元に対して基本SI単位を使用します：
```

jldoctest julia> ucat = UnitCatalogue(); cm = ucat.centi * ucat.meter ;

julia> InternalUnits(length = 3cm) InternalUnits  mass unit:               1 kg  length unit:             3 cm  time unit:               1 s  current unit:            1 A  temperature unit:        1 K  amount unit:             1 mol  luminous intensity unit: 1 cd ```

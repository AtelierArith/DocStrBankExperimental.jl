```
struct Orthotope{D,T} <: AbstractDomain{D,T}
```

軸に整列したオルトトープは、`D` 次元で、要素タイプ `T` を持ち、2つの点 `low_corner` と `high_corner` によって定義されます。`low_corner .≤ high_corner` である必要があることに注意してください。

## フィールド:

  * `corners::SVector{2,SVector{D,T}}`: `corners[1]` = 低コーナー、`corners[2]` = 高コーナー。

## 不変条件（構築時にチェックしない）:

  * `corners[1] .≤ corners[2]`

## コンストラクタ:

  * `Orthotope(low_corner, high_corner)`
  * `Orthotope{T}(low_corner, high_corner)`
  * `Orthotope(corners::SVector{2,SVector{D,T}})`

```
Isotope(symbol, name, Z, A, N, R, M, I, π, T½, mdm, eqm, ra)
```

フィールドを持つ型:

  * `.symbol`: シンボル (`::String`)
  * `.name`: 名前 (`::String`)
  * `.Z`:  原子番号 (`::Int`)
  * `.A`:  原子質量数（amu単位） (`::Int`)
  * `.N`:  中性子数 (`::Int`)
  * `.R`:  rms電荷半径（フェルミ単位） (`::Float64`)
  * `.M`:  *原子* 質量（amu単位） (`::Float64`)
  * `.I`:  核スピン（ħ単位） (`::Rational{Int}`)
  * `.π`:  核状態のパリティ (`::Int`)
  * `.T½`:  寿命（年単位） (`::Float64`)
  * `.mdm`: 核磁気双極子モーメント (`::Float64`)
  * `.eqm`: 核電気四重極モーメント (`::Float64`)
  * `.ra`:  相対存在比（%単位） (`::Float64`)

型 `Isotope` は関数 [`castIsotope`](@ref) を使って作成するのが最適です。

```
castIsotope(;Z=1, A=1, msg=false)
castIsotope(elt::String; A=1, msg=false)
```

フィールドを持つ同位体を作成します

  * `.symbol`: シンボル (`::String`)
  * `.name`: 名前 (`::String`)
  * `.Z`: 原子番号 (`::Int`)
  * `.A`: 原子質量数（amu単位） (`::Int`)
  * `.N`: 中性子数 (`::Int`)
  * `.R`: rms電荷半径（フェルミ単位） (`::Float64`)
  * `.M`: 原子質量（amu単位） (`::Float64`)
  * `.I`: 核スピン（ħ単位） (`::Rational{Int}`)
  * `.π`: 核状態のパリティ (`::Int`)
  * `.ra`: 相対存在比（%単位） (`::Float64`)
  * `.mdm`: 核磁気双極子モーメント (`::Float64`)
  * `.eqm`: 核電気四重極モーメント (`::Float64`)
  * `.T½`: 寿命（年単位） (`::Float64`)

`Z`: 原子番号（核電荷数） `elt`: シンボリック元素名

#### 例:

```
julia> castIsotope("Rb"; A=87) == castIsotope(Z=37, A=87)
true

julia> isotope = castIsotope(Z=1, A=3)
Isotope("³T", "トリチウム", 1, 3, 2, 1.7591, 3.016049281, 1//2, 1, 12.33, 2.97896246, 0.0, nothing)

julia> string(isotope.T½) *  " 秒"
"12.33 秒"

julia> castIsotope(Z=1, A=3, msg=true);
Isotope created: ³T, トリチウム, Z=1, A=3, N=2, R=1.7591, M=3.016049281, I=1/2⁺, μI=2.97896246, Q=0.0, RA=trace, (放射性)
```

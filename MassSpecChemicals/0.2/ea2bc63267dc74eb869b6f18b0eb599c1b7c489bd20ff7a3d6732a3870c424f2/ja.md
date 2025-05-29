```
Isotopomers{T <: AbstractChemical} <: AbstractChemical
```

化学物質は同位体置換の位置によって異なります。

# フィールド

  * `parent`: 同位体置換前の同位体の共有化学構造。
  * `isotopes`: `Vector{Pair{String, Int}}`。同位体置換の同位体-数ペア。

# コンストラクタ

  * `Isotopomers(parent::AbstractChemical, fullformula::String)`
  * `Isotopomers(parent::AbstractChemical, fullelements::Dictionary)`

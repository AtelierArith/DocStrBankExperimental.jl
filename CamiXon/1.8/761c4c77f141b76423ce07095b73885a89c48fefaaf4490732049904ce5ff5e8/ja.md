```
Atom(Z, A, Q, Zc, element, isotope, config)
```

フィールドを持つ型:

  * `.Z`:  原子番号 (`::Int`)
  * `.A`:  原子質量数（amu単位） (`::Int`)
  * `.Q`:  イオン電荷（a.u.単位） (`::Int`)
  * `.Zc`:  リュードベリ電荷（a.u.単位） (`::Int`)
  * `.element`:  (`::Element`)
  * `.isotope`:  (`::Isotope`)
  * `.config`:  電子配置 (`::String`)

型 `Atom` は関数 [`castAtom`](@ref) を使って作成するのが最適です。

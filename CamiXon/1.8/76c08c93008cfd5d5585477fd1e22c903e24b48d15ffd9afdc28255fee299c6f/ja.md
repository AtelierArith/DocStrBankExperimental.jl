```
castAtom(;Z=1, A=1, Q=0, msg=false)
castAtom(elt::String; A=1, Q=0, msg=false)
```

フィールドを持つ原子を作成します：

  * `.Z`:  原子番号 (`::Int`)
  * `.A`:  原子質量数（amu単位） (`::Int`)
  * `.Q`:  イオン電荷（a.u.単位） (`::Int`)
  * `.Zc`:  リュードベリ電荷（a.u.単位） (`::Int`)
  * `.element`:  (`::Element`)
  * `.isotope`:  (`::Isotope`)
  * `.config`:  電子配置 (`::String`)

`elt`: シンボリック元素名

#### 例：

```
julia> castAtom("Rb"; A=87, Q=0) == castAtom(Z=37, A=87, Q=0)
true

julia> castAtom(Z=1, A=3, Q=0)
Atom(1, 3, 0, 1, Element("hydrogen", "H", 1.008), Isotope("³T", "tritium", 1, 3, 2, 1.7591, 3.016049281, 1//2, 1, 12.33, 2.97896246, 0.0, nothing), "1s¹")

julia> atom = castAtom(Z=1, A=3, Q=0, msg=true);
Element created: H, hydrogen, Z=1, weight=1.008
Isotope created: ³T, tritium, Z=1, A=3, N=2, R=1.7591, M=3.016049281, I=1/2⁺, μI=2.97896246, Q=0.0, RA=trace, (radioactive)
Atom: tritium, neutral atom
  symbol: ³T
  atomic charge: Z = 1
  Rydberg charge: Zc = 1
  electron configuration: 1s¹
Atom created: Atom: tritium, neutral atom
  symbol: ³T
  atomic charge: Z = 1
  Rydberg charge: Zc = 1
  electron configuration: 1s¹

julia> atom
Atom(1, 3, 0, 1, Element("hydrogen", "H", 1.008), Isotope("³T", "tritium", 1, 3, 2, 1.7591, 3.016049281, 1//2, 1, 12.33, 2.97896246, 0.0, nothing), "1s¹")

julia> string(atom.isotope.T½) * " seconds"
"12.33 seconds"
```

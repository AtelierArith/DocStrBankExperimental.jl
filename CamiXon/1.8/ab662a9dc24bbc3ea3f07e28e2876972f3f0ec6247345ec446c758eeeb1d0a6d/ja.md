```
listAtoms(Z1::Int, Z2::Int, Q::Int[; fmt=Object])
```

原子番号が `Z1:Z3` の範囲にあり、イオン電荷が `Q` の原子の特性。

出力オプション: `fmt` =  `Object` (デフォルト), `String`, `Info`。

#### 例

```
julia> listAtoms(1,3,0) == listAtoms(1:3,0)
true

julia> listAtoms(1:1, 0; fmt=Info);
Atom: hydrogen, neutral atom
  symbol: ¹H
  atomic charge: Z = 1
  Rydberg charge: Zc = 1
Atom: deuterium, neutral atom
  symbol: ²D
  atomic charge: Z = 1
  Rydberg charge: Zc = 1
Atom: tritium, neutral atom
  symbol: ³T
  atomic charge: Z = 1
  Rydberg charge: Zc = 1
```

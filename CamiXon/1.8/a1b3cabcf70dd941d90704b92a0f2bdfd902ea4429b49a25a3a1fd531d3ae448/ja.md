```
listAtom(Z::Int, A::Int, Q::Int[; fmt=Object])
```

原子番号 `Z`、原子質量数 `A`、イオン電荷 `Q` を持つ原子の特性。

出力オプション: `fmt` =  `Object` (デフォルト), `String`, `Info`.

#### 例:

```
julia> listAtom("H", 3, 0) == listAtom(1, 3, 0)
true

julia> listAtom(1, 3, 0; fmt=Info)
Atom: tritium, neutral atom
  symbol: ³T
  atomic charge: Z = 1
  Rydberg charge: Zc = 1
```

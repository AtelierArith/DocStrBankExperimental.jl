```
listIsotope(Z::Int, A::Int; fmt=Object)
```

原子番号 `Z` と原子質量数 `A` を持つ同位体の特性。

出力オプション: `fmt` =  `Object` (デフォルト), `String`, `Latex`, `Info`.

#### 例:

```
julia> listIsotope(1,3; fmt=Info);
Isotope: tritium-3
  symbol: ³T
  element: tritium
  atomic number: Z = 1
  atomic mass number: A = 3
  neutron number: N = 2
  rms nuclear charge radius: R = 1.7591 fm
  atomic mass: M = 3.016049281 amu
  nuclear spin: I = 1/2 ħ
  parity of nuclear state: π = even
  nuclear magnetic dipole moment: μI = 2.97896246 μN
  nuclear electric quadrupole moment: Q = 0.0 barn
  relative abundance: RA = trace
  lifetime: 12.33 years
```

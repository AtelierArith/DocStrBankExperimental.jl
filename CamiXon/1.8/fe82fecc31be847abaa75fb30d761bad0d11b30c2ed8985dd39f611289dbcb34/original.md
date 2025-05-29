```
dictIsotope
```

Sources: AME2020, LINDC(NDS)-0794 and INDC(NDS)-0833

```
julia> dictIsotope
Dict{Tuple{Int64, Int64}, Tuple{String, String, Int64, Int64, Int64, Float64, Float64, Real, Int64, Float64, Float64, Any, Any}} with 341 entries:
  (71, 175) => ("¹⁷⁵Lu", "lutetium", 71, 175, 104, 5.37, 174.941, 7//2, 1, 1.0e…
  (40, 92)  => ("⁹²Zr", "zirconium", 40, 92, 52, 4.3057, 91.905, 0, 1, 1.0e100,…
  (48, 111) => ("¹¹¹Cd", "cadmium", 48, 111, 63, 4.5845, 110.904, 1//2, 1, 1.0e…
  (72, 176) => ("¹⁷⁶Hf", "hafnium", 72, 176, 104, 5.3286, 175.941, 0, 1, 1.0e10…
  (30, 68)  => ("⁶⁸Zn", "zinc", 30, 68, 38, 3.9658, 67.9248, 0, 1, 1.0e100, 0.0…
  (76, 184) => ("¹⁸⁴Os", "osmium", 76, 184, 108, 5.3823, 183.952, 0, 1, 5.6e13,…
  (54, 129) => ("¹²⁹Xe", "xenon", 54, 129, 75, 4.7775, 128.905, 1//2, 1, 1.0e10…
      ⋮     =>                                ⋮
```

#### Example:

```
julia> get(dictIsotope, (37,87), nothing)
("⁸⁷Rb", "rubidium", 37, 87, 50, 4.1989, 86.90918053, 3//2, -1, 4.97e10, 2.75129, 0.1335, 27.83)

julia> listIsotope(37, 87, fmt=Info)
Isotope: rubidium-87
  symbol: ⁸⁷Rb
  element: rubidium
  atomic number: Z = 37
  atomic mass number: A = 87
  neutron number: N = 50
  rms nuclear charge radius: R = 4.1989 fm
  atomic mass: M = 86.90918053 amu
  nuclear spin: I = 3/2 ħ
  parity of nuclear state: π = odd
  nuclear magnetic dipole moment: μI = 2.75129 μN
  nuclear electric quadrupole moment: Q = 0.1335 barn
  relative abundance: RA = 27.83%
  lifetime: 4.97e10 years
```

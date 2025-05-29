Struct AtomicSpecies

## Description:

> mutable struct to store all (possibly degenerate) information about a particular element<


## Fields:

  * `Z`            – Integer atomic number (i.e. protons in the nucleus)
  * `species_name` – String periodic table symbol for element
  * `mass`   – > Dict{Int, Float64}(isotope::Int, mass::Float64) isotope masses

```
								 > key -1 refers to the average common atomic mass, other keys refer to 
								 > the number of nucleons present in the isotope <
```

## Examples:

  * `AtomicSpeciesData(3, "Li", Dict(Int64, Float64)(-1 => 6.9675, 3 => 3.0308, 4 => 4.02719,

```
	5 => 5.012538, 6 => 6.0151228874, 7 => 7.0160034366, 8 => 8.022486246, 9 => 9.02679019, 
	10 => 10.035483, 11 => 11.04372358, 12 => 12.052517, 13 => 13.06263))`
```

  * `AtomicSpeciesData(47, "Ag", Dict(Int64, Float64)(-1 => 107.8682, 92 => 92.95033,

```
	93 => 93.94373, 94 => 94.93602, 95 => 95.930744, 96 => 96.92397, 97 => 97.92156, 
	98 => 98.9176458, 99 => 99.9161154, 100 => 100.912684, 101 => 101.9117047, 
	102 => 102.9089631, 103 => 103.9086239, 104 => 104.9065256, 105 => 105.9066636, 
	106 => 106.9050916, 107 => 107.9059503, 108 => 108.9047553, 109 => 109.9061102, 
	110 => 110.9052959, 111 => 111.9070486, 112 => 112.906573, 113 => 113.908823, 
	114 => 114.908767, 115 => 115.9113868, 116 => 116.911774, 117 => 117.9145955, 
	118 => 118.91557, 119 => 119.9187848, 120 => 120.920125, 121 => 121.923664, 
	122 => 122.925337, 123 => 123.92893, 124 => 124.93105, 125 => 125.93475, 
	126 => 126.93711, 127 => 127.94106, 128 => 128.94395, 129 => 129.9507))`
```

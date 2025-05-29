```
y2σs(y, ms::MassTuple; k::Int = last(findmin(Tuple(ms))))
```

Maps a pair of variables to the plain of squared masses using a linear transformation. The values [0,1] correspond to the physical limits of the mass squared variables. The physical value

## Arguments

  * `y` : a pair of numbers
  * `ms` : masses of the system as a `MassTuple`, see `ThreeBodyMasses`.
  * `k` : the index for which the variable is not generated. By default, the function picks the coordinates

where the Dalitz plot has the closest shape to the squared fitting box.

## Returns

  * an instance of `MandelstamTuple` with the squared masses.

DecayChainLS docstring:

## Example

The phase space sample with 100 points can be generated as follows: ```julia data = let N = 100

# map random variables to dalitz

_data = mapslices(rand(N,2); dims=2) do xy y2σs(xy, ms) end[:,1]

# select physical

filter!(_data) do σs isphysical(σs, ms) end _data end ````

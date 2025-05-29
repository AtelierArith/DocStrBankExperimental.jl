```
create_random_coordstates(nSamples, d, object=:magicSimplex, precision=10, roundToSteps::Int=0, nTriesMax=10000000)
```

Return an array of `nSamples` $d^2$ dimensional CoordStates. 

Use the `object` to specify the coordinate ranges to [0,1] for 'magicSimplex' or [0, 1/d] for 'enclosurePolytope'.  If `roundToSteps` > 0, round the coordinates to the vertices that divide the range in `roundToSteps`` equally sized sections. Be aware that the resulting distribution of points is generally not uniform.

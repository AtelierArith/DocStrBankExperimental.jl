```
fitcircle(cmd0::String="", arg1=nothing, kwargs...)
```

Find mean position and great [or small] circle fit to points on a sphere.

## Parameters

  * **L** | **norm** :: [Type => Int | []]

    Specify the desired norm as 1 or 2, or use [] or 3 to see both solutions.
  * **F** | **coord** | **coordinates** :: [Type => Str]	`Arg = f|m|n|s|c`

    Only return data coordinates, and append Arg to specify which coordinates you would like.
  * **S** | **small_circle** :: [Type => Number]    `Arg = symmetry_factor`

    Attempt to

To see the full documentation type: $@? fitcircle$

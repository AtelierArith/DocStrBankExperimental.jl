```
create_cubical_complex(cubes::Vector{String}; p::Int=2)
```

Initialize a Lefschetz complex from a cubical complex. The complex is over the rationals if `p=0`, and over `GF(p)` if `p>0`.

The vector `cubes` contains a list of all the highest-dimensional cubes necessary to define the cubical complex. Every cube is represented as a string as follows:

  * d integers, which correspond to the coordinates of a point in d-dimensional Euclidean space
  * a point `.`
  * d integers 0 or 1, which give the interval length in the respective dimension

The first d integers all have to occupy the same number of characters. In addition, if the occupied space is L characters for each coordinate, the coordinates only can take values from 0 to 10^L - 2. This is due to the fact that the boundary operator will add one to certain coordinates, and they still need to be  representable withing the same L digits.

For example, the string `030600.101` corresponds to the point `(3,6,0)` in three dimensions. The dimensions are 1, 0, and 1, and therefore this string corresponds to the cube `[3,4] x [6] x [0,1]`. The same cube could have also been represented by `360.101` or by `003006000.101`.

!!! warning
    Note that the labels all have to have the same format!


# Example

```jldoctest
julia> cubes = ["00.11", "01.01", "02.10", "11.10", "11.01", "22.00"];

julia> lc = create_cubical_complex(cubes);

julia> lc.ncells
17

julia> homology(lc)
3-element Vector{Int64}:
 2
 1
 0
```

```
lefschetz_filtration(lc::LefschetzComplex, fvalues::Vector{Int})
```

Compute a filtration on a Lefschetz subset.

The considered Lefschetz complex is given in `lc`. The vector `fvalues` assigns an integer between 0 and N to every cell in `lc`. For every k the complex `L_k` is given by the closure of all cells with values between 1 and k. The function returns the following variables:

  * `lcsub`: The subcomplex `L_N`
  * `fvalsub`: The filtration on the subcomplex with values 1,...,N

# Example

```jldoctest
julia> labels = ["A","B","C","D","E","F","G"];

julia> simplices = [["A","B","D"],["B","D","E"],["B","C","E"],["C","E","F"],["F","G"]];

julia> sc = create_simplicial_complex(labels,simplices);

julia> filtration = [0,0,0,0,0,0,0,1,1,0,1,2,0,4,2,4,0,5,3,7,6];

julia> lcsub, fvalsub = lefschetz_filtration(sc,filtration);

julia> phinf, phint = persistent_homology(lcsub,fvalsub);

julia> phinf
3-element Vector{Vector{Int64}}:
 [1]
 []
 []

julia> phint
3-element Vector{Vector{Tuple{Int64, Int64}}}:
 []
 [(1, 5), (2, 7), (4, 6)]
 []
```

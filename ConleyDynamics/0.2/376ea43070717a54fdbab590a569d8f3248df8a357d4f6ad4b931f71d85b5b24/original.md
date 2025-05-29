```
lefschetz_filtration(lc::LefschetzComplex, strfilt::Vector{Vector{String}})
```

Compute a filtration on a Lefschetz subset.

The considered Lefschetz complex is given in `lc`. The vector of string vectors `strfilt` contains the necessary simplices to build the filtration. The list `strfilt[k]` contains the simplices that are added at the k-th step, together with their closures. Thus, for every k the complex `L_k` is given by the closure of all cells listed in `strfilt[i]` for `i` between 1 and k. The function returns the following variables:

  * `lcsub`: The subcomplex `L_N`, where `N = length(strfilt)`
  * `fvalsub`: The filtration on the subcomplex with values 1,...,N

# Example

```jldoctest
julia> labels = ["A","B","C","D","E","F","G"];

julia> simplices = [["A","B","D"],["B","D","E"],["B","C","E"],["C","E","F"],["F","G"]];

julia> sc = create_simplicial_complex(labels,simplices);

julia> strfiltration = [["AB","AD","BD"],["BE","DE"],["BCE"],["CF","EF"],["ABD"],["CEF"],["BDE"]];

julia> lcsub, fvalsub = lefschetz_filtration(sc, strfiltration);

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

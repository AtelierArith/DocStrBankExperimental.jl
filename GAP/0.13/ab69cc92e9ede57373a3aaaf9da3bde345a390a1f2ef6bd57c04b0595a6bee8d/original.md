```
GapObj
```

This is the Julia type of all those GAP objects that are not "immediate" (booleans, small integers, FFEs).

# Examples

```jldoctest
julia> typeof(GapObj([1, 2]))          # a GAP list
GapObj

julia> typeof(GapObj(Dict(:a => 1)))   # a GAP record
GapObj

julia> typeof( GAP.evalstr( "(1,2,3)" ) )  # a GAP permutation
GapObj

julia> typeof( GAP.evalstr( "2^64" ) )     # a large GAP integer
GapObj

julia> typeof( GAP.evalstr( "2^59" ) )     # a small GAP integer
Int64

julia> typeof( GAP.evalstr( "Z(2)" ) )     # a GAP FFE
FFE

julia> typeof( GAP.evalstr( "true" ) )     # a boolean
Bool
```

Note that this is Julia's viewpoint on GAP objects. From the viewpoint of GAP, also the pointers to Julia objects are implemented as "non-immediate GAP objects", but they appear as Julia objects to Julia, not "doubly wrapped".

# Examples

```jldoctest
julia> GAP.evalstr( "Julia.Base" )
Base

julia> typeof( GAP.evalstr( "Julia.Base" ) )        # native Julia object
Module
```

One can use `GapObj` as a constructor, in order to convert Julia objects to GAP objects, see [`GapObj(x, cache::GapCacheDict = nothing; recursive::Bool = false)`](@ref) for that.

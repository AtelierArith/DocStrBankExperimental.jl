```
regeneration(F::System; options...)
```

This solves $F=0$ equation-by-equations and returns a [`WitnessSet`](@ref) for every dimension without decomposing them into irreducible components (witness sets that are not decomposed are also called witness supersets).

The implementation is based on the algorithm [u-regeneration](https://arxiv.org/abs/2206.02869) by Duff, Leykin and Rodriguez. 

### Options

  * `sorted = true`: the polynomials in F will be sorted by degree in decreasing order.
  * `max_codim`: the maximal codimension until which witness supersets should be computed.
  * `show_progress = true`: indicate whether the progress of the computation should be displayed.
  * `endgame_options`: [`EndgameOptions`](@ref) for the [`EndgameTracker`](@ref).
  * `tracker_options`: [`TrackerOptions`](@ref) for the [`Tracker`](@ref).
  * `seed`: choose the random seed.

### Example

The following example computes witness sets for a union of two circles.

```julia-repl
julia> @var x y
julia> f = (x^2 + y^2 - 1) * ((x-1)^2 + (y-1)^2 - 1)
julia> W = regeneration([f])
1-element Vector{WitnessSet}:
    Witness set for dimension 1 of degree 4  
```

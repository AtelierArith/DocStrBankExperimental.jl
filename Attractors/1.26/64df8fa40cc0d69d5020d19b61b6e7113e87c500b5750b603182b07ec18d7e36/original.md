```
basins_fractions(basins::AbstractArray [,ids]) → fs::Dict
```

Calculate the state space fraction of the basins of attraction encoded in `basins`. The elements of `basins` are integers, enumerating the attractor that the entry of `basins` converges to (i.e., like the output of [`basins_of_attraction`](@ref)). Return a dictionary that maps attractor IDs to their relative fractions. Optionally you may give a vector of `ids` to calculate the fractions of only the chosen ids (by default `ids = unique(basins)`).

In [Menck2013](@cite) the authors use these fractions to quantify the stability of a basin of attraction, and specifically how it changes when a parameter is changed. For this, see [`global_continuation`](@ref).

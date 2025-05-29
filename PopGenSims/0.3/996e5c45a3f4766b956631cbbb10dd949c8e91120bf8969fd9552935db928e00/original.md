```
simulate(data::PopData; n::Int)
```

Simulate `n` number of individuals per population using per-population allele frequencies derived from a `PopData` object. Returns a new `PopData` object with `n` * `n_populations` samples.

```
simulate(data::PopData; scale::Int)
```

Simulate individuals per population in the same proportions they appear in the PopData using per-population allele frequencies. Simulation volume can be multiplied using `scale`, i.e. if you want to keep the same proportions but generate twice the number of samples, `scale` would be `2`. Returns a new `PopData` object with `n_samples` * `scale` samples.    

**Example**

```julia
julia> cats = @nanycats;

julia> sims = simulate(cats, n = 100)
PopData{Diploid, 9 Microsatellite Loci}
  Samples: 1700
  Populations: 17
  
julia> sims_prop = simulate(cats, scale = 3)
  PopData{Diploid, 9 Microsatellite Loci}
    Samples: 711
    Populations: 17
```

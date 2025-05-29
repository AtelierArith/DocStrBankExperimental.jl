```
subperiodicgroup(num::Integer, ::Val{D}=Val(3), ::Val{P}=Val(2))
subperiodicgroup(num::Integer, D::Integer, P::Integer)
                                                        --> ::SubperiodicGroup{D,P}
```

Return the operations of the subperiodic group `num` of embedding dimension `D` and periodicity dimension `P` as a `SubperiodicGroup{D,P}`.

The setting choices are those of the International Tables for Crystallography, Volume E.

Allowed combinations of `D` and `P` and their associated group names are:

  * `D = 3`, `P = 2`: Layer groups (`num` = 1, …, 80).
  * `D = 3`, `P = 1`: Rod groups (`num` = 1, …, 75).
  * `D = 2`, `P = 1`: Frieze groups (`num` = 1, …, 7).

## Example

```jldoctest
julia> subperiodicgroup(7, Val(2), Val(1))
SubperiodicGroup{2, 1} ⋕7 (𝓅2mg) with 4 operations:
 1
 2
 {m₁₀|½,0}
 {m₀₁|½,0}
```

## Data sources

The symmetry operations returned by this function were originally retrieved from the [Bilbao Crystallographic Database, SUBPERIODIC GENPOS](https://www.cryst.ehu.es/subperiodic/get_sub_gen.html).

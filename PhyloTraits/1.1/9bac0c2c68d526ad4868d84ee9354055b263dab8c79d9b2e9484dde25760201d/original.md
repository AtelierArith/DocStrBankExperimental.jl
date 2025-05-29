```
JC69(rate, relative)
```

Jukes Cantor (1969) nucleic acid substitution model, which has a single rate parameter. `rate` corresponds to the absolute diagonal elements, that is, the rate of change (to any of the other 2 states). Individual rates are `rate`/3. If `relative` is true (default), the transition matrix [`Q`](@ref) is normalized to an average of 1 transition per unit of time: in which case `rate` is set to 1.0.

# examples

```jldoctest
julia> m1 = JC69([0.25], false)
Jukes and Cantor 69 Substitution Model,
absolute rate version
off-diagonal rates equal to 0.25/3.
rate matrix Q:
               A       C       G       T
       A       *  0.0833  0.0833  0.0833
       C  0.0833       *  0.0833  0.0833
       G  0.0833  0.0833       *  0.0833
       T  0.0833  0.0833  0.0833       *

julia> nstates(m1)
4

julia> nparams(m1)
1

julia> m2 = JC69([0.5])
Jukes and Cantor 69 Substitution Model,
relative rate version
off-diagonal rates equal to 1/3
rate matrix Q:
               A       C       G       T
       A       *  0.3333  0.3333  0.3333
       C  0.3333       *  0.3333  0.3333
       G  0.3333  0.3333       *  0.3333
       T  0.3333  0.3333  0.3333       *

julia> nparams(m2)
0
```

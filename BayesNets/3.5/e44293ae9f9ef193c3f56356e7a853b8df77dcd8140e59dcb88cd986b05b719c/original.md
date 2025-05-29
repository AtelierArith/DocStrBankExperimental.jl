```
statistics(
    parent_list::Vector{Vector{Int}},
    ncategories::AbstractVector{Int},
    data::AbstractMatrix{Int},
    )
```

Computes sufficient statistics from a discrete dataset for a Discrete Bayesian Net structure

INPUT:     parents:         list of lists of parent indices         A variable with index i has ncategories[i]         and row in data[i,:]         No acyclicity checking is done     ncategories:         list of variable bin counts, or number of         discrete values the variable can take on, v ∈ {1 : ncategories[i]}     data:         table of discrete values [n×m]         where n is the number of nodes         and m is the number of samples

OUTPUT:     N :: Vector{Matrix{Int}}         a sufficient statistics table for each variable         Variable with index i has statistics table N[i],         which is r × q where         r = ncategories[i] is the number of variable instantiations and         q is the number of parental instantiations of variable i

```
    The r-values are ordered from 1 → ncategories[i]
    The q-values are ordered in the same ordering as ind2sub() in Julia Base
        Thus the instantiation of the first parent (by order given in parents[i])
        is varied the fastest.

    ex:
        Variable 1 has parents 2 and 3, with r₁ = 2, r₂ = 2, r₃ = 3
        q for variable 1 is q = r₂×r₃ = 6
        N[1] will be a 6×2 matrix where:
            N[1][1,1] is the number of time v₁ = 1, v₂ = 1, v₃ = 1
            N[1][2,1] is the number of time v₁ = 1, v₂ = 2, v₃ = 1
            N[1][3,1] is the number of time v₁ = 1, v₂ = 1, v₃ = 2
            N[1][4,1] is the number of time v₁ = 1, v₂ = 2, v₃ = 2
            N[1][5,1] is the number of time v₁ = 1, v₂ = 1, v₃ = 3
            N[1][6,1] is the number of time v₁ = 1, v₂ = 2, v₃ = 3
            N[1][6,2] is the number of time v₁ = 2, v₂ = 1, v₃ = 1
            ...
```

This function uses sparse matrix black magic and was mercilessly stolen from Ed Schmerling.

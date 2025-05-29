```
FrechetCopula
```

The Frechet copula

Fileds:

  * n - number of marginals
  * α - the parameter of the maximal copula
  * β - the parameter of the minimal copula

Constructor

```
FrechetCopula(n::Int, α::Real)
```

The one parameter Frechet copula is a combination of maximal copula with  weight α and independent copula with  weight 1-α.

Constructor

```
FrechetCopula(n::Int, α::Real, β::Real)
```

The two parameters Frechet copula C = α C{max} + β C{min} + (1- α - β) C{⟂}, supported only for n = 2.

```jldoctest
julia> FrechetCopula(4, 0.5)
FrechetCopula(4, 0.5, 0.0)

julia> FrechetCopula(2, 0.5, 0.3)
FrechetCopula(2, 0.5, 0.3)
```

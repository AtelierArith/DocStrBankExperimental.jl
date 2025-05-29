```
DataSetExact(x::AbstractArray, y::AbstractArray, Σ_y::AbstractArray)
DataSetExact(x::AbstractArray, Σ_x::AbstractArray, y::AbstractArray, Σ_y::AbstractArray)
DataSetExact(xd::Distribution, yd::Distribution, dims::Tuple{Int,Int,Int}=(length(xd),1,1))
```

A data container which allows for uncertainties in the independent variables, i.e. $x$-variables. Moreover, the observed data is stored in terms of two probability distributions over the spaces $\mathcal{X}^N$ and $\mathcal{Y}^N$ respectively, which also allows for uncertainties in the observations that are non-Gaussian. For instance, the uncertainties associated with a given observation might follow a Cauchy, t-student, log-normal or some other smooth distribution.

Examples:

```julia
using InformationGeometry, Distributions
X = product_distribution([Normal(0, 1), Cauchy(2, 0.5)])
Y = MvTDist(2, [3, 8.], [1 0.5; 0.5 3])
DataSetExact(X, Y, (2,1,1))
```

!!! note
    Uncertainties in the independent $x$-variables are optional for `DataSetExact`, and can be set to zero by wrapping the `x`-data in a `InformationGeometry.Dirac` "distribution". The following illustrates numerically equivalent ways of encoding a dataset whose uncertainties in the $x$-variables is zero:

    ```julia
    using InformationGeometry, Distributions, LinearAlgebra
    DS1 = DataSetExact(InformationGeometry.Dirac([1,2]), MvNormal([5,6], Diagonal([0.1, 0.2].^2)))
    DS2 = DataSetExact([1,2], [5,6], [0.1, 0.2])
    DS3 = DataSet([1,2], [5,6], [0.1, 0.2])
    ```

    where `DS1 == DS2 == DS3` will evaluate to `true`.


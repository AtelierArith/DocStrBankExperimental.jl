The `DataSet` type is a versatile container for storing data. Typically, it is constructed by passing it three vectors `x`, `y`, `sigma` where the components of `sigma` quantify the standard deviation associated with each y-value. Alternatively, a full covariance matrix can be supplied for the `ydata` instead of a vector of standard deviations. The contents of a `DataSet` `DS` can later be accessed via `xdata(DS)`, `ydata(DS)`, `ysigma(DS)`.

Examples:

In the simplest case, where all data points are mutually independent and have a single $x$-component and a single $y$-component each, a `DataSet` consisting of four points can be constructed via

```julia
DataSet([1,2,3,4], [4,5,6.5,7.8], [0.5,0.45,0.6,0.8])
```

or alternatively by

```julia
using LinearAlgebra
DataSet([1,2,3,4], [4,5,6.5,7.8], Diagonal([0.5,0.45,0.6,0.8].^2))
```

where the diagonal covariance matrix in the second line is equivalent to the vector of standard deviations supplied in the first line.

For measurements with multiple components, it is also possible to enter them as a `Matrix` where the columns correspond to the respective components.

```julia
DataSet([0, 0.5, 1], [1 100; 2 103; 3 108], [0.5 8; 0.4 5; 0.6 10])
```

Note that if the uncertainty matrix is square, it may be falsely interpreted as a covariance matrix instead of as the columnwise specification of standard deviations.

More generally, if a dataset consists of $N$ points where each $x$-value has $n$ many components and each $y$-value has $m$ many components, this can be specified to the `DataSet` constructor via a tuple $(N,n,m)$ in addition to the vectors `x`, `y` and the covariance matrix. For example:

```julia
X = [0.9, 1.0, 1.1, 1.9, 2.0, 2.1, 2.9, 3.0, 3.1, 3.9, 4.0, 4.1]
Y = [1.0, 5.0, 4.0, 8.0, 9.0, 13.0, 16.0, 20.0]
Cov = Diagonal([2.0, 4.0, 2.0, 4.0, 2.0, 4.0, 2.0, 4.0])
dims = (4, 3, 2)
DS = DataSet(X, Y, Cov, dims)
```

In this case, `X` is a vector consisting of the concatenated x-values (with 3 components each) for 4 different data points. The values of `Y` are the corresponding concatenated y-values (with 2 components each) of said 4 data points. Clearly, the covariance matrix must therefore be a positive-definite $(m \cdot N) \times (m \cdot N)$ matrix.

```
spgbox!(f, g!, x::AbstractVecOrMat; lower=..., upper=..., options...)
```

Minimizes function `f` starting from initial point `x`, given the function to compute the gradient, `g!`. `f` must be of the form `f(x)`, and `g!` of the form `g!(g,x)`, where `g` is the gradient vector to be modified. It modifies the `x` vector, which will contain the best solution found (see `spgbox` for a non-mutating alternative). 

Optional lower and upper box bounds can be provided using optional arguments `lower` and `upper`, which can be provided as the fourth and fifth arguments or with keyword parameters.

Returns a structure of type `SPGBoxResult`, containing the best solution found in `x` and the final objective function in `f`.

Alternativelly, a single function that computes the function value and the gradient can be provided, using:

```
spgbox(fg!, x; lower=..., upper=..., options...)
```

The `fg!` must be of the form `fg!(g,x)` where `x` is the current point and `g` the array that stores the gradient. And it must return the function value.   

# Examples

```julia-repl
julia> f(x) = x[1]^2 + x[2]^2

julia> function g!(g,x)
           g[1] = 2*x[1]
           g[2] = 2*x[2]
       end
```

## Without bounds

```julia-repl
julia> x = [1.0, 2.0]

julia> spgbox!(f,g!,x)

 SPGBOX RESULT: 

 Convergence achieved. 

 Final objective function value = 0.0
 Sample of best point = Vector{Float64}[ 0.0, 0.0]
 Projected gradient norm = 0.0

 Number of iterations = 3
 Number of function evaluations = 3
```

## With bounds

```julia-repl
julia> x = [3.0, 4.0]

julia> spgbox!(f,g!,x,lower=[2.,-Inf])

 SPGBOX RESULT: 

 Convergence achieved.

 Final objective function value = 4.0
 Sample of best point = Vector{Float64}[ 2.0, 0.0]
 Projected gradient norm = 0.0

 Number of iterations = 1
 Number of function evaluations = 1
```

## With a single function to compute the function and the gradient

```julia-repl
julia> function fg!(g,x)
           g[1] = 2*x[1]
           g[2] = 2*x[2]
           fx = x[1]^2 + x[2]^2
           return fx
       end
fg! (generic function with 1 method)

julia> x = [1.0, 2.0];

julia> spgbox(fg!,x)

 SPGBOX RESULT: 

 Convergence achieved. 

 Final objective function value = 0.0
 Sample of best point = Vector{Float64}[ 0.0, 0.0]
 Projected gradient norm = 0.0

 Number of iterations = 3
 Number of function evaluations = 3
```

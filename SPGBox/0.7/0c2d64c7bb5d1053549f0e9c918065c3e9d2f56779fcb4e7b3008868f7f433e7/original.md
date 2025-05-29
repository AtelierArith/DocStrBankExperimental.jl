```
spgbox(f, g!, x::AbstractVecOrMat; lower=..., upper=..., options...)`
```

See `spgbox!` for additional help.

Minimizes function `f` starting from initial point `x`, given the function to compute the gradient, `g!`.  `f` must be of the form `f(x)`, and `g!` of the form `g!(g,x)`, where `g` is the gradient vector to be modified. 

Optional lower and upper box bounds can be provided using optional keyword arguments `lower` and `upper`.

```
spgbox(fg!, x::AbstractVecOrMat; lower=..., upper=..., options...)`
```

Given a single function `fg!(g,x)` that updates a gradient vector `g` and returns the function value, minimizes the function.  

These functions return a structure of type `SPGBoxResult`, containing the best solution found in `x` and the final objective function in `f`.

These functions *do not* mutate the `x` vector, instead it will create a (deep)copy of it (see `spgbox!` for the in-place alternative). 

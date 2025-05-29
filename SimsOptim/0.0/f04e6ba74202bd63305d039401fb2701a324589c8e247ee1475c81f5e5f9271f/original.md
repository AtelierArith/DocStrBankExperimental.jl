```
optimize(
    f::Function,
    g::Function,
    x0::AbstractVector,
    m::Csolve;
    <keyword arguments>
)
```

solves the linear system `f(x) = 0` using Chris Sims' `csolve` method

# Arguments

`f::Function`: the objective function to minimize `g::Function`: a function that computes the gradient of `f` `x0::AbstractVector`: an initial guess for the optimizing input `m::Csolve`: an instance of the Csolve structure

# Keyword Arguments

`f_tol::Real = 1e-14`: tolerance for successive evaluations of the objective function `g_tol::Real = 1e-8`: tolerance for norm of objective's gradient `x_tol::Real = 1e-32`: tolerance for successive steps of the input `iterations::Int = 1000`: maximum number of steps to take `δ::Real = 1e-6`: differencing interval for the numerical gradient `α::Real = 1e-3`: tolerance on the rate of descent `verbose::Bool = false`: print messages to REPL

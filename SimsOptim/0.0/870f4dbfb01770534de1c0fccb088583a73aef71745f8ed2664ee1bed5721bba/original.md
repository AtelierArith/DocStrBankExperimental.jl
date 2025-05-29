```
optimize(
    f::Function,
    g::Function,
    x0::AbstractVector,
    H0::AbstractMatrix,
    m::Csminwel;
    <keyword arguments>
)
```

solve the equation `f(x) = 0` using Chris Sims' `csminwel` algorithm

# Arguments

`f::Function`: the objective function to minimize `g::Function`: a function that computes the gradient of `f` `x0::AbstractVector`: an initial guess for the optimal input `H0::AbstractMatrix`: an initial guess for the Hessian matrix `m::Csminwel`: an instance of the Csminwel structure

# Keyword Arguments

`f_tol::Real = 1e-14`: tolerance for successive evaluations of the objective function `g_tol::Real = 1e-8`: tolerance for norm of objective's gradient `x_tol::Real = 1e-32`: tolerance for successive steps of the input `iterations::Int = 100`: maximum number of steps to take `δ::Real = 1e-6`: differencing interval for the numerical gradient `α::Real = 1e-3`: tolerance on the rate of descent `verbose::Bool = false`: print messages to REPL

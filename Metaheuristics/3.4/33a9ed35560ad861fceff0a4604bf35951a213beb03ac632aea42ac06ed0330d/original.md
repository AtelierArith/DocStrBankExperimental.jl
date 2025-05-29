```julia
    SA(;
        x_initial::Vector = zeros(0),
        N::Int = 500,
        tol_fun::Real= 1e-4,
        information = Information(),
        options = Options()
    )
```

Parameters for the method of Simulated Annealing (Kirkpatrick et al., 1983).

Parameters:

  * x_intial: Inital solution. If empty, then SA will generate a random one within the bounds.
  * N: The number of test points per iteration.
  * tol_fun: tolerance value for the Metropolis condition to accept or reject the test point as current point.

# Example

```jldoctest
julia> f(x) = sum(x.^2)
f (generic function with 1 method)

julia> optimize(f, [-1 -1 -1; 1 1 1.0], SA())
+=========== RESULT ==========+
  iteration: 60
    minimum: 5.0787e-68
  minimizer: [-2.2522059499734615e-34, 3.816133503985569e-36, 6.934348004465088e-36]
    f calls: 29002
 total time: 0.0943 s
+============================+

julia> optimize(f, [-1 -1 -1; 1 1 1.0], SA(N = 100, x_initial = [1, 0.5, -1]))
+=========== RESULT ==========+
  iteration: 300
    minimum: 1.99651e-69
  minimizer: [4.4638292404181215e-35, -1.738939846089388e-36, -9.542441152683457e-37]
    f calls: 29802
 total time: 0.0965 s
+============================+
```

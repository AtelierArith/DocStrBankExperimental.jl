```
G, H, e = arxar(d::InputOutputData, na::Int, nb::Union{Int, Vector{Int}}, nd::Int)
```

Estimate the ARXAR model `Ay = Bu + v`, where `v = He` and `H = 1/D`, using generalized least-squares method. 

The ARXAR abbreviation stands for "bivariate parametric autoregressive model with exogenous input". For more information see Söderström - Convergence properties of the generalized least squares identification method, 1974. 

# Arguments:

  * `d`: iddata
  * `na`: order of A
  * `nb`: number of coefficients in B, the order is determined by `nb + inputdelay - 1`. In MISO estimation it takes the form `nb = [nb₁, nb₂...]`.
  * `nd`: order of D

# Keyword Arguments:

  * `H = nothing`: prior knowledge about the AR noise model
  * `inputdelay = ones(Int, size(nb))`: optional delay of input, inputdelay = 0 results in a direct term, takes the form inputdelay = [d₁, d₂...] in MISO estimation
  * `λ = 0`: `λ > 0` can be provided for L₂ regularization
  * `estimator = \`: e.g. `\,tls,irls,rtls`, the latter three require `using TotalLeastSquares`
  * `δmin = 10e-4`: Minimal change in the power of e, that specifies convergence.
  * `iterations = 10`: maximum number of iterations.
  * `verbose = false`: if true, more information is printed

See also [`plr`](@ref), [`arx`](@ref).

# Example:

```
julia> N = 500 
500

julia> sim(G, u) = lsim(G, u, 1:N)[1][:]
sim (generic function with 1 method)

julia> A = tf([1, -0.8], [1, 0], 1)
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
1.0z - 0.8
----------
   1.0z

Sample Time: 1 (seconds)
Discrete-time transfer function model

julia> B = tf([0, 1], [1, 0], 1)
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Int64}}
1
-
z

Sample Time: 1 (seconds)
Discrete-time transfer function model

julia> G = minreal(B / A)
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
   1.0
----------
1.0z - 0.8

Sample Time: 1 (seconds)
Discrete-time transfer function model

julia> D = tf([1, 0.7], [1, 0], 1)
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
1.0z + 0.7
----------
   1.0z

Sample Time: 1 (seconds)
Discrete-time transfer function model

julia> H = 1 / D
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
   1.0z
----------
1.0z + 0.7

Sample Time: 1 (seconds)
Discrete-time transfer function model

julia> u, e = randn(1, N), randn(1, N)
[...]

julia> y, v = sim(G, u), sim(H * (1/A), e) # simulate process
[...]

julia> d = iddata(y .+ v, u, 1)
InputOutput data of length 500 with 1 outputs and 1 inputs

julia> na, nb , nd = 1, 1, 1
(1, 1, 1)

julia> Gest, Hest, res = arxar(d, na, nb, nd)
(G = TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
   0.9987917259291642
-------------------------
1.0z - 0.7937837464682017

Sample Time: 1 (seconds)
Discrete-time transfer function model, H = TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
          1.0z
-------------------------
1.0z + 0.7019519225937721

Sample Time: 1 (seconds)
Discrete-time transfer function model, e = [...]
```

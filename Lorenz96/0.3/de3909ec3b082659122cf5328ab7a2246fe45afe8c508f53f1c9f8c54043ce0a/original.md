```
X = L96(Float32)
```

Integrates the Lorenz1996 model. Standard parameters

```
L96(::Type{T}=Float64,              # number format for RHS
::Type{Tprog}=T;                    # number format for prognostic variables
N::Int=10_000,                      # number of time steps
n::Int=36,                          # number of variables
X::Array{Float64,1}=zeros(36),      # initial conditions
α::Real=1.0,                        # friction parameter
F::Float64=8.0,                     # forcing constant
s::Float64=1.0,                     # scaling
η::Float64=0.01,                    # strength of initial perturbation at X[1] if no X provided
Δt::Float64=0.01,                   # time step
scheme::String="RK4"                # time integration scheme
output::Bool=false                  # return every time step?
```

# Examples

```jldoc
julia> X1 = L96(Float32);
julia> X2 = L96(Float32,n=6,Δt=0.005);
julia> X3 = L96(Float16,Float32);
```

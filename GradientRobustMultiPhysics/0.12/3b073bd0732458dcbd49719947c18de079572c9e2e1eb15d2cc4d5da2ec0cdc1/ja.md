```julia
using DifferentialEquations

function jacobi_matrix(f, u, p, t)
    # Calculate the Jacobian matrix of the system
    n = length(u)
    J = zeros(n, n)
    h = 1e-8  # Perturbation size

    for i in 1:n
        u_perturbed = copy(u)
        u_perturbed[i] += h
        J[:, i] = (f(u_perturbed, p, t) .- f(u, p, t)) / h
    end

    return J
end
```

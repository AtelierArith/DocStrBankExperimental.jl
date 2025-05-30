```
GPModel <: JuMP.AbstractModel
```

A model type for geometric programming problems. It extends JuMP's model functionality to handle geometric programming constraints and transformations.

Geometric programs involve:

  * Minimizing posynomials or maximizing monomials
  * Subject to monomial equality constraints (= 1)
  * And posynomial inequality constraints (≤ 1)

# Example

```julia
using GSOpt

# Create a geometric programming model
model = GPModel()

# Add variables (must be positive in geometric programming)
@variable(model, x >= 1)
@variable(model, y >= 1)

# Set objective (minimize a posynomial)
@objective(model, Min, 2x + 3y + 4x*y)

# Add constraints
@constraint(model, x*y <= 10)  # Posynomial inequality
@constraint(model, x*y^2 == 20)  # Monomial equality

# Solve the model
optimize!(model)

# Get results
value(x)
value(y)
objective_value(model)
```

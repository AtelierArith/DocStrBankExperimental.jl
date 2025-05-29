```
ConstraintList
```

Stores the set of constraints included in a trajectory optimization problem. Includes a list of both the constraint types [`AbstractConstraint`](@ref) as well as the knot points at which the constraint is applied. Each constraint is assumed to apply to a contiguous set of knot points.

A `ConstraintList` supports iteration and indexing over the `AbstractConstraint`s, and iteration of both the constraints and the indices of the knot points at which they apply via `zip(cons::ConstraintList)`.

Constraints are added via the [`add_constraint!`](@ref) method, which verifies that the constraint dimension is consistent with the state and control dimensions at the knot points at which  they are applied. 

The total number of constraints at each knot point can be queried using the [`num_constraints`](@ref) method.

# Constructors

```
ConstraintList(nx, nu)
ConstraintList(n, m, N)
ConstraintList(models)
```

Where `nx` and `nu` are `N`-dimensional vectors that specify the state and control dimension  at each knot point. If these are the same for the entire trajectory, the user can use the  2nd constructor. Alternatively, they can be constructed automatically from `models`, a  vector of `DiscreteDynamics` models.

```
add_constraint!(cons::ConstraintList, con::AbstractConstraint, inds::UnitRange, [idx, sig, diffmethod])
```

Add constraint `con` to `ConstraintList` `cons` for knot points given by `inds`.

Use `idx` to determine the location of the constraint in the constraint list. `idx=-1` (default) adds the constraint at the end of the list.

The `FunctionSignature` and `DiffMethod` used to evaluate the constraint can be specified by the `sig` and `diffmethod` keyword arguments, respectively.

# Example

Here is an example of adding a goal and control limit constraint for a cartpole swing-up.

```julia
# Dimensions of our problem
n,m,N = 4,1,51    # 51 knot points

# Create our list of constraints
cons = ConstraintList(n,m,N)

# Create the goal constraint
xf = [0,π,0,0]
goalcon = GoalConstraint(xf)
add_constraint!(cons, goalcon, N)  # add to the last time step

# Create control limits
ubnd = 3
bnd = BoundConstraint(n,m, u_min=-ubnd, u_max=ubnd, idx=1)  # make it the first constraint
add_constraint!(cons, bnd, 1:N-1)  # add to all but the last time step

# Indexing
cons[1] === bnd                            # (true)
cons[2] === goal                           # (true)
allcons = [con for con in cons]
cons_and_inds = [(con,ind) in zip(cons)]
cons_and_inds[1] == (bnd,1:n-1)            # (true)
```

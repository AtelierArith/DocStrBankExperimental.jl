```
jacobian!(∇c, con::AbstractConstraint, z, i=1)       # stage constraint
jacobian!(∇c, con::AbstractConstraint, z1, z2, i=1)  # coupled constraint
```

Evaluate the constraint `con` at knot point `z`. By default, this method will attempt to call

```
jacobian!(∇c, con, x)
```

if `con` is a `StateConstraint`,

```
jacobian!(∇c, con, u)
```

if `con` is a `ControlConstraint`, or

```
jacobian!(∇c, con, x, u)
```

if `con` is a `StageConstraint`. If `con` is a `CoupledConstraint` the constraint should define

```
jacobian!(∇c, con, z, i)
```

where `i` determines which Jacobian should be evaluated. E.g. if `i = 1`, the Jacobian with respect to the first knot point's stage and controls is calculated.

# Automatic Differentiation

If `con` is a `StateConstraint` or `ControlConstraint` then this method is automatically defined using ForwardDiff.

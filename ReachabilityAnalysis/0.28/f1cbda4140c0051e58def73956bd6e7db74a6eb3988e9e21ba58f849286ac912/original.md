```
normalize(system::AbstractSystem)
```

Transform a mathematical system to a normalized (or canonical) form.

### Input

  * `system` – system; it can be discrete or continuous

### Output

Either the same system if it already conforms to a canonical form, or a new system otherwise.

### Notes

The normalization procedure consists of transforming a given system type into a "canonical" format that is used internally. More details are given below.

### Algorithm

The implementation of `normalize` exploits `MathematicalSystems`'s' types, which carry information about the problem as a type parameter.

Homogeneous ODEs of the form $x' = Ax, x ∈ \mathcal{X}$ are canonical if the associated problem is a `ConstrainedLinearContinuousSystem` and `A` is a matrix. This type does not handle non-deterministic inputs.

Note that a `LinearContinuousSystem` does not consider constraints on the state-space (such as an invariant); to specify state constraints, use a `ConstrainedLinearContinuousSystem`. If the passed system is a `LinearContinuousSystem` (i.e. no constraints) then the normalization fixes a universal set (`Universe`) as the constraint set.

The generalization to canonical systems with constraints and possibly time-varying non-deterministic inputs is considered next. These systems are of the form $x' = Ax + u, u ∈ \mathcal{U}, x ∈ \mathcal{X}$. The system type is `ConstrainedLinearControlContinuousSystem`, where `A` is a matrix, `X` is a set and `U` is an input, that is, any concrete subtype of `AbstractInput`.

If `U` is not given as an input, normalization accepts either a `LazySet`, or a vector of `LazySet`s. In these cases, the sets are wrapped around an appropriate concrete input type.

If the system does not conform to a canonical form, the implementation tries to make the transformation; otherwise an error is thrown. In particular, ODEs of the form $x' = Ax + Bu$ are mapped into $x' = Ax + u, u ∈ B\mathcal{U}$, where now $u$ has the same dimensions as $x$.

The transformations described above are analogous in the discrete case, i.e. $x_{k+1} = A x_k$ and $x_{k+1} = Ax_{k} + u_k, u_k ∈ \mathcal{U}, x_k ∈ \mathcal{X}$ for the linear and affine cases respectively.

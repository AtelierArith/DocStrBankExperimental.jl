```
Operator(ceed::Ceed; qf, dqf=QFunctionNone(), dqfT=QFunctionNone(), fields)
```

Creates a libCEED `CeedOperator` object using the given Q-function `qf`, and optionally its derivative and derivative transpose.

An array of fields must be provided, where each element of the array is a tuple containing the name of the field (as a string or symbol), the corresponding element restriction, basis, and vector.

# Examples

Create the operator that builds the Q-data associated with the mass matrix.

```
build_oper = Operator(
    ceed,
    qf=build_qfunc,
    fields=[
        (:J, mesh_rstr, mesh_basis, CeedVectorActive()),
        (:w, ElemRestrictionNone(), mesh_basis, CeedVectorNone()),
        (:qdata, sol_rstr_i, BasisNone(), CeedVectorActive())
    ]
)
```

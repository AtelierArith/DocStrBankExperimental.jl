```
PropositionalLogiset(table) <: AbstractPropositionalLogiset
```

A logiset of propositional interpretations, wrapping a [Tables](https://github.com/JuliaData/Tables.jl)' table of real/string/categorical values.

# Examples

This structure can be used to check propositional formulas:

```julia
using SoleData, MLJBase

X = PropositionalLogiset(MLJBase.load_iris())

φ = parseformula(
    "sepal_length > 5.8 ∧ sepal_width < 3.0 ∨ target == "setosa"";
    atom_parser = a->Atom(parsecondition(SoleData.ScalarCondition, a; featuretype = SoleData.VariableValue))
)

check(φ, X, 10) # Check the formula on a single instance

satmask = check(φ, X) # Check the formula on the whole dataset

slicedataset(X, satmask)
slicedataset(X, (!).(satmask))
```

See also [`AbstractLogiset`](@ref), [`AbstractAssignment`](@ref).

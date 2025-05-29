```
fix_discrete_variables([var_value::Function = value,] model::GenericModel)
```

Modifies `model` to convert all binary and integer variables to continuous variables with fixed bounds of `var_value(x)`.

## Return

Returns a function that can be called without any arguments to restore the original model. The behavior of this function is undefined if additional changes are made to the affected variables in the meantime.

## Notes

  * An error is thrown if semi-continuous or semi-integer constraints are present (support may be added for these in the future).
  * All other constraints are ignored (left in place). This includes discrete constraints like SOS and indicator constraints.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x, Bin, start = 1);

julia> @variable(model, 1 <= y <= 10, Int, start = 2);

julia> @objective(model, Min, x + y);

julia> undo_relax = fix_discrete_variables(start_value, model);

julia> print(model)
Min x + y
Subject to
 x = 1
 y = 2

julia> undo_relax()

julia> print(model)
Min x + y
Subject to
 y ≥ 1
 y ≤ 10
 y integer
 x binary
```

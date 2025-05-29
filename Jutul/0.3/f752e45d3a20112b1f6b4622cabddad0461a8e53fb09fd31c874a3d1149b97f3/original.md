Designate the function as updating a secondary variable.

A generic evaluator is then defined, together with a function for getting the dependencies of that function upon the state. This is most easily documented with an example. If we define the following function annotated with the macro when updating the array containing the values of `MyVarType` realized for some model:

```julia
@jutul_secondary function some_fn!(target, var::MyVarType, model, a, b, c, ix)
    for i in ix
        target[i] = a[i] + b[i] / c[i]
    end
end
```

The purpose of the macro is to translate this into two functions. The first defines for the dependencies of the function with respect to the fields of the state (primary variables, secondary variables and parameters):

```julia
function get_dependencies(var::MyVarType, model)
   return (:a, :b, :c)
end
```

The second function defines a generic version that takes in state, and automatically expands the set of dependencies into `getfield` calls.

```julia
function update_secondary_variable!(array_target, var::MyVarType, model, state, ix)
    some_fn!(array_target, var, model, state.a, state.b, state.c, ix)
end
```

Note that the input names of arguments 4 to end-1 matter, as these will be fetched from state, exactly as written.

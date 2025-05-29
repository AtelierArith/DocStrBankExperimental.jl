```
create_model(
    case::Case,
    modeltype::EnergyModel,
    m::JuMP.Model;
    check_timeprofiles::Bool = true,
    check_any_data::Bool = true,
)
```

Create the model and call all required functions.

## Arguments

  * `case::Case` - The case type represents the chosen time structure, the included [`Resource`](@ref)s and the 𝒳 and potential coupling between the 𝒳. It is explained in more detail in its *[docstring](@ref Case)*.
  * `modeltype` - Used modeltype, that is a subtype of the type `EnergyModel`.
  * `m` - the empty `JuMP.Model` instance. If it is not provided, then it is assumed that the input is a standard `JuMP.Model`.

## Keyword arguments

  * `check_timeprofiles=true` - A boolean indicator whether the time profiles of the individual nodes should be checked or not. It is advised to not deactivate the check, except if you are testing new components. It may lead to unexpected behaviour and potential inconsistencies in the input data, if the time profiles are not checked.
  * `check_any_data::Bool=true` - A boolean indicator whether the input data is checked or not. It is advised to not deactivate the check, except if you are testing new features. It may lead to unexpected behaviour and even infeasible models.

!!! note "Old to new"
    We provide additional methods for translating the old dictionary to the new case types.


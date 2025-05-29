First we need to define the action space. In the [`MultiArmBanditsEnv`](@ref) environment, the possible actions are `1` to `k` (which equals to `length(env.true_values)`).

!!! note
    Although we decide to return an action space of `Base.OneTo`  here, it is not a hard requirement. You can return anything else (`Tuple`, `Distribution`, etc) that is more suitable to describe your problem and handle it correctly in the `you_env(action)` function. Some algorithms may require that the action space must be of `Base.OneTo`. However, it's the algorithm designer's job to do the checking and conversion.


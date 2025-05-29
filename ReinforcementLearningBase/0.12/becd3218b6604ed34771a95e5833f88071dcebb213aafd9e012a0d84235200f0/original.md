Environment contains chance player and the probability is unknown. Usually only a dummy action is allowed in this case.

!!! note
    The chance player ([`chance_player`](@ref)`(env)`) must appears in the result of [`players`](@ref)`(env)`. The result of `action_space(env, chance_player)` should only contains one dummy action.


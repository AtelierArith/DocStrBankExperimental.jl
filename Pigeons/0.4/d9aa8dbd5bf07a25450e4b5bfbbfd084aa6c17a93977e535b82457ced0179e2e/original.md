Uses `DynamicPPL` i.e. `Turing`'s backend to construct the log density.

To work with Pigeons `DynamicPPL` or `Turing` needs to be imported into the current session.

  * `model`: A `DynamicPPL.Model`.

  * `context`: Either `DynamicPPL.DefaultContext` for evaluating the full joint, or `DynamicPPL.PriorContext` for evaluating only the prior.

  * `dimension`: The total number of scalar values observed in a single random sample from `model`. It is used by the `LogDensityProblems` and `LogDensityProblemsAD` interfaces when a gradient-based sampler is used as explorer in models with static computational graphs.

    !!! warning
        Explorers targeting models with dynamic computational graphs should not depend on the value of this field.

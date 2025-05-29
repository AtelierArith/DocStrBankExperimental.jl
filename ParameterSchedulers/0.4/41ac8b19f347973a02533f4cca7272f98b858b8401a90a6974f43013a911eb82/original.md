```
Scheduler{T, F} <: Optimiser.AbstractRule
Scheduler(constructor, schedules::AbstractSchedule...)
Scheduler(constructor; field_a = schedule_a, field_b = schedule_b, ...)
```

Wrap one or more schedules and optimizer together with a `Scheduler`. On each call to [`Optimisers.apply!`](https://fluxml.ai/Optimisers.jl/dev/api/#Optimisers.apply!), the schedules are iterated and `constructor` is used to invoke an optimization rule with updated parameters. The `Scheduler` can be used anywhere an Optimisers.jl optimizer is used.

If passed a single schedule and optimizer rule, the scheduler updates the learning, `opt.eta`. To adjust multiple hyperparameters, pass in multiple schedules as arguments or keywords. These will be iterated in order and passed onto to `constructor` (i.e. `constructor` should accept the appropriate number of arguments/keywords).

# Arguments

  * `constructor`: a constructor that creates an optimization rule given some   parameters (e.g. `Optimisers.AdamW`; note the lack of `()`)
  * `schedules`: the list of optimization rule hyperparameters to schedule as   multiple (named) arguments

# Examples

```julia
# cosine annealing schedule for Descent
julia> opt = Scheduler(Descent, CosAnneal(l0 = 0.1, l1 = 0.8, period = 10));

# schedule learning rate and momentum of Momentum
julia> opt = Scheduler(Momentum, CosAnneal(l0 = 0.1, l1 = 0.8, period = 10), Exp(0.999, 0.8));

# schedule the weight decay term of AdamW with a custom fixed learning rate
julia> opt = Scheduler(AdamW, eta = 1e-4, decay = Exp(1e-3, 0.7));
```

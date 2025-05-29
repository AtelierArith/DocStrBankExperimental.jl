```
TargetNetwork(network::Approximator; sync_freq::Int = 1, ρ::Float32 = 0f0)
```

Wraps an Approximator to hold a target network that is updated towards the model of the  approximator. 

  * `sync_freq` is the number of updates of `network` between each update of the `target`.
  * ρ ( ho) is "how much of the target is kept when updating it".

The two common usages of TargetNetwork are 

  * use ρ = 0 to totally replace `target` with `network` every sync_freq updates.
  * use ρ < 1 (but close to one) and sync_freq = 1 to let the target follow `network` with polyak averaging.

Implements the `RLBase.optimise!(::TargetNetwork, ::Gradient)` interface to update the model with the gradient and the target with weights replacement or Polyak averaging.

Note to developers: `model(::TargetNetwork)` will return the trainable Flux model  and `target(::TargetNetwork)` returns the target model and `target(::Approximator)` returns the non-trainable Flux model. See the RLCore documentation.

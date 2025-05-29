```
train!(gen_fn::GenerativeFunction, data_generator::Function,
       update::ParamUpdate,
       num_epoch, epoch_size, num_minibatch, minibatch_size; verbose::Bool=false)
```

Train the given generative function to maximize the expected conditional log probability (density) that `gen_fn` generates the assignment `constraints` given inputs, where the expectation is taken under the output distribution of `data_generator`.

The function `data_generator` is a function of no arguments that returns a tuple `(inputs, constraints)` where `inputs` is a `Tuple` of inputs (arguments) to `gen_fn`, and `constraints` is an `ChoiceMap`.

`conf` configures the optimization algorithm used.

`param_lists` is a map from generative function to lists of its parameters. This is equivalent to minimizing the expected KL divergence from the conditional distribution `constraints | inputs` of the data generator to the distribution represented by the generative function, where the expectation is taken under the marginal distribution on `inputs` determined by the data generator.

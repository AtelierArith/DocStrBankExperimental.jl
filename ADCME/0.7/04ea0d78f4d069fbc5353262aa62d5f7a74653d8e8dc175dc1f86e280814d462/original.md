categorical(n::Union{PyObject, Integer}; kwargs...)

`kwargs` has a keyword argument `logits`, a 2-D Tensor with shape `[batch_size, num_classes]`.   Each slice `[i, :]` represents the unnormalized log-probabilities for all classes.

Output the expectation of `pushforward.post_processing(X)`, where `X` follows the distribution defined by `pushforward.optimization_layer` applied to `θ`.

This function is differentiable, even if `pushforward.post_processing` isn't.

`random_choice(weights)` randomly chooses a value from `1` to `n`, where `n` is the number of elements in `weights`. The probability that `k` is chosen is proportional to `weights[k]`. The `weights` must be nonnegative and not all zero.

`random_choice(dict)` choose a random key `k` from `dict` with weight proportional to `dict[k]`. Thus, `dict` must be of type `Dict{S, T<:Real}`.

function artifact*reject(signal::TimeSeries, anom*dict::Dict{Int, Vector{Int}}; epoch*length::Integer=30, subepoch*length::Integer=5)::Vector{Vector{<:AbstractFloat}};

This function removes from a signal the sub-epochs which contain artifacts.  It requires a `TimeSeries` and a `Dict{Int, Vector{Int}}`, hereby termed  `anom_dict` (for anomaly dictionary). 

`anom_dict` is understood to be such that `anom_dict[i] = [n₁, …, nₖ]` means the `i`th epoch has artifacts at sub-epochs `n₁, ..., nₖ`.

The return value is a segmented signal (`Vector{Vector<:AbstractFloat}}`), each  of whose segments corresponds to an epoch with its artifcat-contaminated  sub-epochs removed. In other words, if the `result`   holds   the   return    value   of    this    function,    `result[i]` contains   what   is   left   from    the    `i`th    epoch    after    removing its   contaminated   sub-epochs.   It   is   possible   that   `result[i]`    is empty, if all sub-epochs of epoch `i` contained artifacts.

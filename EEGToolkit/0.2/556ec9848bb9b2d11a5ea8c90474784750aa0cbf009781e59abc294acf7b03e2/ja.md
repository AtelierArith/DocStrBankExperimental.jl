`freq_band(spec::Union{PSD}, lower::AbstractFloat, upper::AbstractFloat)`

与えられた `PSD` に対して、周波数帯 `[lower, upper]` 内のパワーを持つ `Vector{<:AbstractFloat}` を返します。

reinit!: function that set all the entries at void except the mandatory x

`reinit!(:: NLPAtX, x :: AbstractVector, l :: AbstractVector; kwargs...)`

`reinit!(:: NLPAtX; kwargs...)`

Note: if `x` or `lambda` are given as keyword arguments they will be prioritized over the existing `x`, `lambda` and the default `Counters`.

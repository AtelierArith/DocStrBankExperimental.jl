```
rqa(R; kwargs...)
```

Calculate all RQA parameters of a recurrence matrix `R`. See the functions referred to below for the definition of the different parameters and the default values of the arguments. Using this function is much more efficient than calling all individual functions one by one.

## Return

The returned value contains the following entries, which can be retrieved as from a dictionary (e.g. `results[:RR]`, etc.):

  * `:RR`: recurrence rate (see [`recurrencerate`](@ref))
  * `:DET`: determinsm (see [`determinism`](@ref))
  * `:L`: average length of diagonal structures (see [`dl_average`](@ref))
  * `:Lmax`: maximum length of diagonal structures (see [`dl_max`](@ref))
  * `:DIV`: divergence (see [`divergence`](@ref))
  * `:ENTR`: entropy of diagonal structures (see [`dl_entropy`](@ref))
  * `:TREND`: trend of recurrences (see [`trend`](@ref))
  * `:LAM`: laminarity (see [`laminarity`](@ref))
  * `:TT`: trapping time (see [`trappingtime`](@ref))
  * `:Vmax`: maximum length of vertical structures (see [`vl_max`](@ref))
  * `:VENTR`: entropy of vertical structures (see [`vl_entropy`](@ref))
  * `:MRT`: mean recurrence time (see [`meanrecurrencetime`](@ref))
  * `:RTE` recurrence time entropy (see [`rt_entropy`](@ref))
  * `:NMPRT`: number of the most probable recurrence time (see [`nmprt`](@ref))

All the parameters returned by `rqa` are `Float64` numbers, even for parameters like `:Lmax`, `:Vmax` or `:NMPRT` which are integer values. In the case of empty histograms (e.g. no existing vertical lines less than the keyword `lminvert`) the average and maximum values (`:L`, `:Lmax`, `:TT`, `:Vmax`, `:MRT`) are returned as `0.0` but their respective entropies (`:ENTR`, `:VENTR`, `:RTE`) are returned as `NaN`.

## Keyword Arguments

Standard keyword arguments are the ones accepted by the functions listed below, i.e. `theiler`, `lmin`, and `border`:

  * `theiler` is used to define a "Theiler window" around the central diagonal or "line of identity" (LOI): a region of points that are excluded in the calculation of RQA parameters, in order to rule out self-recurrences and apparent recurrences for smooth or high resolution data. The LOI is excluded by default for matrices of the types `RecurrenceMatrix` or `JointRecurrenceMatrix`, but it is included for matrices of the type `CrossRecurrenceMatrix`. `theiler=0` means that the whole matrix is scanned for lines. `theiler=1` means that the LOI is excluded. In general, `theiler=n` means that the `n` central diagonals are excluded (at both sides of the LOI, i.e. actually `2n-1` diagonals are excluded).
  * `lmin` is used to define the minimum line length in the parameters that describe the distributions of diagonal or vertical lines (it is set as 2 by default).
  * `border` is used to avoid border effects in the calculation of `:TREND` (cf. [`trend`](@ref)).

In addition `theilerdiag`, `lmindiag` may be used to declare specific values that override the values of `theiler` and `lmin` in the calculation of parameters related to diagonal structures. Likewise, `theilervert` and `lminvert` can be used for the calculation of parameters related to vertical structures.

The keyword argument `onlydiagonal` (`false` by default) can be set to `true` in order to restrict the analysis to the recurrence rate and the parameters related to diagonal structures (`:RR`, `:DET`, `:L`, `:Lmax`, `:DIV` and `:ENTR`), which makes this function slightly faster.

## Transitional note on the returned type

In older versions, the `rqa` function returned a `NamedTuple`, and in future versions it is planned to return a `Dict` instead. In both cases, the results can be indexed with square brackets and `Symbol` keys, as `result[:RR]`, `result[:DET]`, etc. However, named tuples can also be indexed with "dot syntax", e.g. `result.RR`, whereas this will not be possible with dictionaries, and there are other differences in the indexing and iteration of those two types.

In order to facilitate the transition between versions, this function currently returns a `RQA` object that essentially works as a dictionary, but can also be indexed with the dot syntax (logging a deprecation warning). The returned type can also be specified as a first argument of `rqa` in order to replicate the output of different versions:

  * `rqa(NamedTuple, R...)` to obtain the output of the older version (as in 1.3).
  * `rqa(Dict, R...)` to obtain the output of the planned future version.
  * `rqa(RQA, R...)` to obtain the default current output (same as `rqa(R...)`)
  * `rqa(DT,R...)` to obtain the output as `DT` which is a subtype of `AbstractDict` (e.g. `rqa(OrderedDict,R...)` returns an `OrderedDict`)

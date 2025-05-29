```
BinningParameters(binstart, binend, binwidth; covectors=I(4))
BinningParameters(binstart, binend; numbins, covectors=I(4))
```

Describes a 4D parallelepided histogram in a format compatible with experimental Inelasitic Neutron Scattering data. See `generate_mantid_script_from_binning_parameters` to convert [`BinningParameters`](@ref) to a format understandable by the [Mantid software](https://www.mantidproject.org/), or [`load_nxs`](@ref) to load [`BinningParameters`](@ref) from a Mantid `.nxs` file.

The coordinates of the histogram axes are specified by multiplication of `(q,ω)` with each row of the `covectors` matrix, with `q` given in [R.L.U.]. Since the default `covectors` matrix is the identity matrix, the default axes are `(qx, qy, qz, ω)` in absolute units.

The convention for the binning scheme is that:

  * The left edge of the first bin starts at `binstart`
  * The bin width is `binwidth`
  * The last bin contains `binend`
  * There are no "partial bins;" the last bin may contain values greater than `binend`.

A `value` can be binned by computing its bin index:

```jl
    coords = covectors * value
    bin_ix = 1 .+ floor.(Int64, (coords .- binstart) ./ binwidth)
```

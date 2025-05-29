```
res2fresnel(results::Vector{Result}, fresnelfile::AbstractString)
res2fresnel(resultfile::AbstractString, fresnelfile::AbstractString)
```

Create an HFSS-compatible "Fresnel table" file from `results`, the vector of `Result` objects returned by  the `analyze` function.  If the first positional argument is an `AbstractString`, it is  assumed to be the name of a PSSFSS results file, from which the vector of results will be read.

Since Fresnel tables contain data for only a single ϕ value, if the input `result` vector contains data for multiple ϕ values, only the value with minimum magnitude will be used.

Fresnel tables may be formatted to contain only reflection coefficients (for a so-called "opaque" structure), or they  may contain both reflection and transmission coefficients (a "non-opaque" structure). An opaque structure is one for which the s21 partition of the generalized scattering matrix is identically zero  for all frequencies and scan angles.  The correct format to be written will be selected automatically by `res2fresnel`.

## Requirements for Fresnel Table Compatibility

The data in `results` must satisfy the following requirements:

1. Incidence angles rather than incremental phasings must be used.
2. θ angles must begin at 0 and be uniformly spaced up to the maximum θ value present.
3. The increment in θ values must divide evenly into 90.
4. If multiple frequencies are present, then they must have a uniform spacing.

A Fresnel table must contain θ values equally spaced between 0 and 90, inclusive.   If the `results` vector provided as input does not contain θ values all the way to 90, then the scattering matrix values  corresponding to the maximum provided θ value will be copied into the remaining angular "slots" as necessary to provide  a complete Fresnel table.

There are some limitations on the type of unit cell geometry that should be used for creating Fresnel tables.  First, a Fresnel  table contains data for only a single ϕ value.  This means that the geometry being analyzed must be such that the scattering matrix of the structure is essentially independent of ϕ.  As a counterexample, a strip grid is not a suitable structure, since its scattering properties are strongly dependent on ϕ.  Second, a Fresnel table records only co-polarized (TE → TE and TM → TM) transmission and reflection coefficients.  This means that the structure being analyzed must not  generate cross-polarized (TE → TM or TM → TE) transmission or reflection coefficients of significant amplitude.

Fresnel tables consider only incidence from a single "front" region. When creating the Fresnel table, the front region is taken  to be Region 1 of the PSSFSS model (i.e. the first layer present in the PSSFSS `strata` vector). 

### Additional Requirements for Non-Opaque Structures

When used in an HFSS SBR+ model, the scattering properties read from the Fresnel table are applied to a zero-thickness surface, so that the transmitted ray is launched from the same "hit" point of the surface that was encountered by the incident  ray. Because of this, the phase reference plane for both input and output ports of the PSSFSS model should be located  at this front surface (i.e. the first interface plane in the `strata` vector).  This is accomplished by specifying zero  width for the first `Layer` object (i.e. using `Layer()` for the first layer), and then specifying the final layer's width to be the negative of the sum of all the other layer widths in the `strata` vector. The negative width value shifts the output port reference plane to coincide with that of the input port.  As an example:

```julia
strata = [Layer(), Layer(width=2mm, ϵᵣ=2.2) Layer(width=3.3mm, ϵᵣ=3.0), Layer(width=2mm, ϵᵣ=2.2), Layer(width=-7.3mm)]
```

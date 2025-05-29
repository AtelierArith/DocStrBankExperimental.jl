```
SeisNMO(in,out,parameters; <keyword arguments>)
```

# Arguments

  * `in::String`: Input file - Seis format.
  * `out::String`: Output file - Seis format.
  * `parameters` : list of the keyword arguments for the function SeisMute.

# Keyword arguments

  * `group="gather"` : Options are all, some or gather
  * `key=["imx","imy"]` : Defines type of gather
  * `itrace=1` : Initial trace number
  * `ntrace=10000` : Total number of traces to process at once

# Example

```
julia> param = Dict(:tmute=>0.0, :vmute=>10000, :taper=>0.05,:dt=>0.01)
julia> SeisMute(filein,fileout, param,group="some")
```

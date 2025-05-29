```
SeisBandPass(in,out,parameters; <keyword arguments>)
```

# Arguments

  * `in::String`: Input file - Seis format
  * `out::String`: Output file - Seis format.
  * `parameters` : list of the keyword arguments for the function SeisBandPass.

# Keyword arguments

  * `group="gather"` : Options are all, some or gather
  * `key=["imx","imy"]` : Defines type of gather
  * `itrace=1` : Initial trace number
  * `ntrace=10000` : Total number of traces to process at once

# Example

```
julia> param = Dict(:fa>=0,:fb=>0,:fc=>60,:fd=>80)
julia> SeisBandPass(filein,fileout, param,group="all")
```

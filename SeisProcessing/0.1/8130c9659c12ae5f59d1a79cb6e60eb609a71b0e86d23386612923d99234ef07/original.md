```
SeisGain(in,out,parameters; <keyword arguments>)

Gain a group of traces. Input and output are file names.
```

# Arguments

  * `in::String`: Input file - Seis format
  * `out::String`: Output file - Seis format.
  * `parameters` : list of the keyword arguments for the function SeisGain.

# Keyword arguments

  * `group="gather"` : Options are all, some or gather
  * `key=["imx","imy"]` : Defines type of gather
  * `itrace=1` : Initial trace number
  * `ntrace=10000` : Total number of traces to process at once

# Example

```
julia> param = Dict(:dt=>0.01,:kind=>"time",:coef=>[2.0,0.0],:normal=>0)
julia> SeisGain(filein,fileout, param,group="all")
```

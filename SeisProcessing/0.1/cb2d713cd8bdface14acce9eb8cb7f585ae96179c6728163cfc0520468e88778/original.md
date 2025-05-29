```
  SeisProcessFile(in,out,operators,parameters;<keyword arguments>)
```

Run processing flows that read and write from disk

f is a function that has the following syntax: d2 = f(d1,param), where param is list of keyword arguments for the function. Note that f can be a vector of functions. They will be executed sequentially on the same group of traces.

# Arguments

  * `in`: input filename of type String or Array{String,1} - Seis format
  * `out`: output filenames of type String or Array{String,1} - Seis format
  * `operators`
  * `parameters`

# Keyword arguments

  * `group="gather"` : Options are all, some or gather
  * `key=["imx","imy"]` : Defines type of gather
  * `itrace=1` : Initial traces
  * `ntrace=10000` : Total number of traces to process at once

# Example

Apply a bandpass filter to a seismic cube sequentially, by shot gather. Assume dt is equal to 0.002.

```
julia> operators = [SeisBandPass]
julia> param = [Dict(:dt=>0.002, :fa=>20,:fb=>30,:fc=>80,:fd=>90)]
julia> SeisProcessFile(filein,fileout,operators,param,key=["sx"])
```

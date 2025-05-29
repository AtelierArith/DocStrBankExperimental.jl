```
  SeisProcessFile(in1,in2,out,operators,parameters;<keyword arguments>)
```

Run processing flows that read from 2 files and write to disk

# Arguments

  * `in1::String`: input filename - Seis format.
  * `in2::String`: input filename - Seis format.
  * `out::String`: output filename - Seis format.
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

```
SeisWrite(filename,d,h,extent;<keyword arguments>)
```

Write seismic data in seis format

# Arguments

  * `filename` : Name of file to write/generate
  * `d`: seismic data
  * `h::Array{Header,1}`: headers as 1d array with elements of type Header
  * `extent::Extent` : extent of the data (try *names(Extent)* to see the information this contains)
  * `itrace=1` : First trace number to write

*Credits: AS, 2015*

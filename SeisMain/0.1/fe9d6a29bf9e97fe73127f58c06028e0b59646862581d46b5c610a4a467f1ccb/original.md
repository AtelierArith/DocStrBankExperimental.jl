```
SeisRead(filename;<keyword arguments>)
```

Read seismic data from a given filename in seis format. The format is comprised of three elements:

  * a text file (data extent) with geometry information
  * a binary file containing data (@data@)
  * a binary file containing headers (@headers@)

# Keyword arguments

  * `group="all"` : Options are all, some or gather
  * `key=["imx","imy"]`
  * `itrace=1` : Number of trace where the function starts reading
  * `ntrace=10000` : Total number of traces to read

# Out

  * d: data as 2d array
  * h: headers as 1d array
  * extent: extent of the data (try *fieldnames(Extent)* to see the information this contains)

# Example

```julia
d,h,ext = SeisRead(filename)
```

*Credits: AS, 2015*

```
SeisReadHeaders(filename;<keyword arguments>)
```

Read the headers of a input file in seis format

# Arguments

  * `group="all"` : Options are all, some or gather
  * `key=[]`
  * `itrace=1` : Number of trace where the function starts reading
  * `ntrace=100` : Total number of traces to read

# Example

```julia
h = SeisRead(filename)
```

*Credits: AS, 2015*

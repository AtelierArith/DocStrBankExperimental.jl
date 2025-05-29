```
SeisSort(in, out;<keyword arguments>)
```

Sort a seis file using its header words

# Arguments

  * `in`: input filename >> a text file with information about data extent, data and header file names; a binary file containing data and a binary file containing headers.
  * `out`: output filename

# Keyword arguments

  * `key=["imx","imy"]`
  * `rev=false` : sort headers in decreasing order
  * `ntrace=1000` : number of traces to read at a time

# Output

file `out` is created with data sorted.

*Credits: AS, 2015*

```
SeisWindow(in,out;<keyword arguments>)
```

Window a seis file using header words.

# Arguments

  * `in::String`: filename of input
  * `out::String`: filename of output

# Keyword arguments

  * `key=[]`
  * `minval=[]`
  * `maxval=[]`

note that windowing along the time axis is achieved by using the key "t".

*Credits: AS, 2015*

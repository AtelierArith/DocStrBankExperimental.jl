```
SeisWindowPatch(in,out;<keyword arguments>)
```

Window a seis file using header words.

# Arguments

  * `in::String`: filename of input
  * `out::String`: filename of output
  * `key=[]`: note that windowing along the time axis is achieved by using the key "t".
  * `minval=[]`
  * `maxval=[]`
  * `it_nt=9e9`

*Credits: AS, FC, 2017*

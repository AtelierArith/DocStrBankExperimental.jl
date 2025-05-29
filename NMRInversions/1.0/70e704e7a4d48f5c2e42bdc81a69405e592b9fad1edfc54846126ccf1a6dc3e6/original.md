```
input2D(seq, x, y)
```

A structure containing the following fields:

  * `seq` is the 2D pulse sequence (e.g. IRCPMG)
  * `x_direct` is the direct dimension acquisition parameter (e.g. the times when you aquire CPMG echoes).
  * `x_indirect` is the indirect dimension acquisition parameter (e.g. all the delay times τ in your IR sequence).
  * `data` is the 2D data matrix.

It can be used as an input for the invert function.

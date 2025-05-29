`cut(io::IO=stdout,string;width=displaysize(io)[2]-2,after=",",before="")`

This  function prints to `io` the  string argument cut across several lines for improved display. It can take the following keyword arguments:

  * width:  the cutting width
  * after:  cut after these chars
  * before: cut before these chars

```julia-rep1
julia> cut(string(collect(1:50)))
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21,
 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40,
 41, 42, 43, 44, 45, 46, 47, 48, 49, 50]
```

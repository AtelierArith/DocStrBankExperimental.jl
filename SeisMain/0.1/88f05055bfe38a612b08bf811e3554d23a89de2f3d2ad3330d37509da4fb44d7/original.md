```
  SeisProcess(in,out,operators,parameters;<keyword arguments>)
```

Run processing flows that read and write from disk

f is a function that has the following syntax: d2,h2 = f(d1,h1,e1,param), where param is list of keyword arguments for the function. Note that f can be a vector of functions. They will be executed sequentially on the same group of traces.

# Arguments

  * `in::String`: input filename
  * `out::String`: output filenames
  * `key=[]`

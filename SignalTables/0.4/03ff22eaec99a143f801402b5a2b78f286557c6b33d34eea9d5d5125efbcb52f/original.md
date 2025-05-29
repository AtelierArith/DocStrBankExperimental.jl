```
getSignalNames(signalTable; getVar=true, getPar=true, getMap=true)::Vector{String}
```

Returns a string vector of the signal names that are present in signalTable (including independent signal names).

  * If getVar=true, Var(..) variables are included.
  * If getPar=true, Par(..) variables are included.
  * If getMap=true, Map(..) variables are included.

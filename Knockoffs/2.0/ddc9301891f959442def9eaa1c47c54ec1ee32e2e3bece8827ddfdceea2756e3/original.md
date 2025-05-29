```
MK_statistics(T0::Vector, Tk::Vector)
```

Compute regular knockoff statistics tau and W. 

# Inputs

  * `T0`: p-vector of importance score for original variables
  * `Tk`: p-vector of importance score for knockoff variables

# output

  * `W`: coefficient difference statistic `W[i] = abs(T0[i]) - abs(Tk[i])`

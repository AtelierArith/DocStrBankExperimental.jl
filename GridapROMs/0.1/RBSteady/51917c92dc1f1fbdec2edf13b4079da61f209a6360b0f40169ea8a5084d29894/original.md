```
struct PODReduction{A,B} <: DirectReduction{A,B}
  red_style::A
  norm_style::B
  nparams::Int
end
```

Reduction by means of a truncated POD. The field `nparams` indicates the number of parameters selected for the computation of the snapshots

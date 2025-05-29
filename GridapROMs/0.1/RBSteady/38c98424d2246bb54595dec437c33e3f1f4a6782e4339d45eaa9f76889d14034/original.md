```
struct TTSVDReduction{B} <: DirectReduction{TTSVDRanks,B}
  red_style::TTSVDRanks
  norm_style::B
  nparams::Int
end
```

Reduction by means of a TTSVD. The field `nparams` indicates the number of parameters selected for the computation of the snapshots

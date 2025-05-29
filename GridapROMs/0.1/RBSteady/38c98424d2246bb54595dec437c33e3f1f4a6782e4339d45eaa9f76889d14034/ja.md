```
struct TTSVDReduction{B} <: DirectReduction{TTSVDRanks,B}
  red_style::TTSVDRanks
  norm_style::B
  nparams::Int
end
```

TTSVDによる削減。フィールド `nparams` は、スナップショットの計算に選択されたパラメータの数を示します。

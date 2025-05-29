```
struct PODReduction{A,B} <: DirectReduction{A,B}
  red_style::A
  norm_style::B
  nparams::Int
end
```

切断されたPODによる削減。フィールド `nparams` はスナップショットの計算に選択されたパラメータの数を示します。

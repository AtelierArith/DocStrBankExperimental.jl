```
factor_shift(IA::IntermediateAlmostBlockDiagonal, ipivot::AbstractArray{I}, scrtch)
```

ほぼブロック対角行列 `IA[i]` の中間表現を因数分解し、次のブロック `IA[i+1]` の準備のためにシフトします。

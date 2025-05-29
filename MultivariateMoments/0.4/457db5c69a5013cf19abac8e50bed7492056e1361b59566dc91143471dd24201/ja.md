```
function compute_support!(ν::MomentMatrix, rank_check, solver) end
```

`ν`の`support`フィールドを`rank_check`で評価されたランクを使用して、低ランク分解を用いて`solver`で計算します。

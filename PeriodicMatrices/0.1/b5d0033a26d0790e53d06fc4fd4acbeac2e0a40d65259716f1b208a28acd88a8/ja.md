```
 ws_pschur(A::Array{Float64,3}) -> (QIND, SIND, ALPHAR, ALPHAI, BETA, SCAL, IWORK, DWORK)
```

関数 `pschur!` が追加の割り当てを避けて SLICOT ベースのラッパー `mb03vw!` と `mb03bd!` を呼び出すための作業スペースを割り当てます。

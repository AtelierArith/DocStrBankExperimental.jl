```
fp_rpa(tm::TaylorModel1{Interval{T},T})
fp_rpa(tm::RTaylorModel1{Interval{T},T})
```

`tm` の TaylorModel1 を、係数が `Float64` の TaylorModel1 に変換します。累積誤差は余りに加算されます。展開区間の中点は、正確に表現可能な値でない場合は優先的に切り捨てられます。

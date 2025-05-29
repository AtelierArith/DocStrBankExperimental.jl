```
getNmax(f::Vector{T}, start::Int, stop:Int) where T<:Real
getNmax(f::Vector{T}, itr::UnitRange) where T<:Real
```

区間 $start ≤ n ≤ stop$ の境界で切り捨てられた離散関数 $f[n]$ の絶対最大に対応するインデックス。条件: $f'[n]$ は区間 ${start,stop}$ で単調増加または単調減少でなければならない。

注: 逆放物線の場合、アルゴリズムは極値のインデックスを見つけます。通常の放物線は二つの最大値を持ちます（探索区間の境界で）。この場合、アルゴリズムは二つのうちの高い方のインデックスを見つけます。決定できない場合、結果は start になります。

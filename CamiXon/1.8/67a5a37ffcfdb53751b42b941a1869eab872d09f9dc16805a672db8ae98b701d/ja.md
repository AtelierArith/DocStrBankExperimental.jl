```
getNmin(f::Vector{T}, start::Int, stop:Int) where T<:Real
getNmin(f::Vector{T}, itr::UnitRange) where T<:Real
```

区間 $start ≤ n ≤ stop$ の境界で切り取られた離散関数 $f[n]$ の絶対最小値に対応するインデックス。条件: $f'[n]$ は区間 ${start,stop}$ で単調増加または単調減少でなければならない。

注: 通常の放物線の場合、アルゴリズムは最小値のインデックスを見つけます。切り取られた逆放物線には（区間の境界で）2つの最小値があります。この場合、アルゴリズムは2つのうちの低い方のインデックスを見つけます。決定できない場合、結果は start になります。

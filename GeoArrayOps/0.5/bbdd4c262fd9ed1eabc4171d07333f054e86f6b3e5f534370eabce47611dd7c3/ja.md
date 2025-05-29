```
slope(dem::Matrix{<:Real}; cellsize=1.0, method=Horn())
```

スロープは、Burrough, P. A. と McDonell, R. A. (1998年、地理情報システムの原則) に定義されているように、セルとその隣接セルとの間の変化率です。

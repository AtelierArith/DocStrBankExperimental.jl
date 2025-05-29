```
WallConstraint{P,T}
```

制約の形式

```
   制約違反なし
```

---

```
          p1 * ///
             |////
```

制約なし  |////        制約   違反      |–––> v   違反                  |////                  |////               p2 * /// ––––––––––––––––––––- 	   制約違反なし

$$
(x - p1)^T v \leq 0
$$

ただし $x = [x[x], x[y]]$, $p1 = [x1,y1]$, $p2 = [x2,y2]$ $v = [xv,yv]$。p1 と p2 の順序は関係ありません。

# コンストラクタ:

```julia
WallConstraint(n, x1::SVector{P}, y1::SVector{P}, x2::SVector{P}, y2::SVector{P}, xv::SVector{P}, yv::SVector{P}, x=1, y=2)
```

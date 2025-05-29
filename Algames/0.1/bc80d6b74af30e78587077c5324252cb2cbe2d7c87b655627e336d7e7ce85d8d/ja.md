```
Wall3DConstraint{P,T}
```

制約の形式

```
   制約違反なし
```

---

  * –––– p1 * ///              |////

制約なし  |////        制約   違反      |–––> v   違反                  |////                  |//// p3 * –––– p2 * ///

```
             -
         -|  制約違反なし
  p3 *c.v.|
 -    |   |               -
```

  * |  制約あり|  |           - |  違反 | |       - |         ||   -

p1 * –––– * p2    |  c.v. -    |  -   -|     制約違反なし ––––––––––––––––––––- 	   制約違反なし p1, p2, p3 の点は3D空間における平行六面体を形成します。

$$
(x - p1)^T v \leq 0
$$

ここで $x = [x[x], x[y], x[z]]$, $p1 = [x1,y1,z1]$, $p2 = [x2,y2,z2]$, $p3 = [x3,y3,z3]$, $v = [xv,yv,zv]$。

# コンストラクタ:

```julia
Wall3DConstraint(n, x1::SVector{P}, y1::SVector{P}, z1::SVector{P}, x2::SVector{P}, y2::SVector{P}, z2::SVector{P},  x3::SVector{P}, y3::SVector{P}, z3::SVector{P}, xv::SVector{P}, yv::SVector{P}, x=1, y=2, z=3)
```

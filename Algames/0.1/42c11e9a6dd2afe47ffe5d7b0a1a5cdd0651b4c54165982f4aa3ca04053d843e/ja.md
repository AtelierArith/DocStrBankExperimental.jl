```
CylinderConstraint{P,T}
```

制約の形式

```
   制約違反なし
```

---

```
			制約なし
			違反
			       r
                 ---->
             ////|////  ^
             ////|////  |
```

制約なし  /// v ///  |     制約   違反      ////^////  |l    違反                  ////|con.  |                  ////|vio.  |                  / p * ///  |

---

```
   制約違反なし
```

pは原点、vは方向、lは長さ、rは半径です

# コンストラクタ:

```julia
CylinderConstraint(n, p1::SVector{P}, p2::SVector{P}, p3::SVector{P},
	v::SVector{P},  l::SVector{P}, r::SVector{P}, x=1, y=2, z=3)
```

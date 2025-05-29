```
ENU(bounds::Bounds{LLA},
	lla_ref::LLA = center(bounds),
	datum::Ellipsoid = WGS84)
```

LLA境界をENUに変換

明確な変換はありませんが、現時点では、入力境界に含まれるすべての点を含む最小境界を返します。

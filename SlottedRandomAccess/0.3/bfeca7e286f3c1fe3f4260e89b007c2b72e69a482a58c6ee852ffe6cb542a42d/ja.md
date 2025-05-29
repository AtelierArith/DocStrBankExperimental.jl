```
@enum ReplicaPowerStrategy SamePower IndependentPower
```

レプリカの電力が特定のRAフレーム内の特定のユーザーに対してどのように決定されるかを指定するために使用される列挙型。

# 値

  * `SamePower`: 特定のRAフレーム内の特定のユーザーに対して、すべてのレプリカが同じ電力を持つ。
  * `IndependentPower`: 各レプリカが各スロットで独立した電力を持つ。

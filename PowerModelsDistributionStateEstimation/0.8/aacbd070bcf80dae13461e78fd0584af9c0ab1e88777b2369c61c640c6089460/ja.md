```
update_generator_bounds!(data; p_min, p_max, q_min, q_max)
```

すべての発電機のために、上限（p*max、q*max）および下限（p*min、q*min）のアクティブおよびリアクティブパワーの境界を自動的に設定する関数です。最大で4つのアクティブフェーズがあり、すべてが同じ境界を持つと仮定しています。

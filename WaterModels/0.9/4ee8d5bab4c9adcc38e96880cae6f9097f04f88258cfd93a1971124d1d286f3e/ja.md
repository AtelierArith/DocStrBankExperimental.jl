```
objective_des(wm::AbstractWaterModel)
```

ネットワーク設計 (des) 問題の仕様に対する目的関数を設定し、返します。デフォルトでは、すべての設計パイプと時間インデックスにわたる離散パイプ抵抗を選択するコストが最小化されます。つまり、目的は

$$
\text{minimize} ~ \sum_{t \in \mathcal{T}}
\sum_{(i, j) \in \mathcal{A}^{\textrm{des}}_{t}} c_{ijt} z_{ijt},
$$

ここで、$\mathcal{T}$ は時間インデックスの集合、$\mathcal{A}^{\textrm{des}}_{t}$ は時間インデックス $t$ で利用可能な設計パイプの集合、$c_{ijt}$ は時間インデックス $t$ で設計パイプ $(i, j)$ を設置するコスト、$z_{ijt}$ は設計パイプが建設のために選択されるかどうかを示すバイナリ変数です (選択される場合は 1、そうでない場合は 0)。

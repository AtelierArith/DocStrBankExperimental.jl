```
mean_obliquity(jd) -> m_eps
```

### 目的

与えられたユリウス日付の平均黄道傾斜を返します。

### 説明

この関数は[`co_nutate`](@ref)手続きによって使用されます。

### 引数

  * `jd`: ユリウス日付

### 出力

  * `m_eps`: 黄道の平均傾斜（ラジアン）

### 例

```jldoctest
julia> using AstroLib

julia> mean_obliquity(jdcnv(1978,01,7,11, 01))
0.4091425159336512
```

### 注意事項

平均黄道傾斜（`eps0`）を求めるために使用されるアルゴリズムは、USNO Circular 179に記載されていますが、IAUの採用に関する正式な参考文献は、Hilton et al., 2006, Celest.Mech.Dyn.Astron. 94, 351. 2000のようです。

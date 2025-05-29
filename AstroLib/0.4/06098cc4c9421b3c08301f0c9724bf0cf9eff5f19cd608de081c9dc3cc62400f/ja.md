```
true_obliquity(jd) -> t_eps
```

### 目的

与えられたユリウス日付の真の黄道傾斜を返します。

### 説明

この関数は[`co_aberration`](@ref)手続きによって使用されます。

### 引数

  * `jd`: ユリウス日付。

### 出力

  * `t_eps`: 黄道の真の傾斜（ラジアン）

### 例

```jldoctest
julia> using AstroLib

julia> true_obliquity(jdcnv(1978,01,7,11, 01))
0.4090953896211926
```

### 注意事項

この関数は[`mean_obliquity`](@ref)を呼び出します。

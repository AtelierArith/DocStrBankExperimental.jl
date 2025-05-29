```
Domain([T=Float64,] dimensions, lower_boundary, upper_boundary, [mapping])
```

三次元デカルト領域のサイズ `dimensions`、最初の二つの座標方向に沿って周期的で、第三の座標方向に沿って `lower_boundary` と `upper_boundary` によって区切られています。

# 引数

  * `T::DataType = Float64`: 領域内の座標とフィールドに使用される型。
  * `dimensions::Tuple`: 領域のサイズ。第三の次元は単一の値として指定でき、その場合、領域は $x_3=0$ から始まると仮定されるか、最小および最大の $x_3$ 値を持つタプルとして指定できます。省略された場合、カスタム `mapping` が提供されない限り、デフォルトで $x_3 ∈ [0,1]$ と仮定されます。
  * `lower_boundary`, `upper_boundary`: 境界定義。
  * `mapping`: デフォルトの線形マッピングの代わりに、区間 $[0,1]$ から $x_3$ 値の範囲への非線形マッピング。マッピングは、マッピングとその導関数を表す二つの関数のタプルとして指定するか、事前定義された [`SinusoidalMapping`](@ref) を使用して指定できます。前者の場合、指定された場合は `dimensions` の第三要素は無視されます; 後者の場合、マッピングは領域のサイズに調整されます。

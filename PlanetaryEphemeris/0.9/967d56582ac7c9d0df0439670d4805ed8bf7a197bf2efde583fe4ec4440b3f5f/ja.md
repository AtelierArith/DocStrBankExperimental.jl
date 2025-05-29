```
selecteph2jld2(sseph::TaylorInterpolant, bodyind::T, tspan::S) where {T <: AbstractVector{Int}, S <: Number}
```

`sseph`に含まれる天体のエフェメリスを、インデックス`bodyind`を持つ天体のために、次のように名付けられた`.jld2`ファイルに保存します。

```
"sseph" * sseph内の小惑星の数 * "ast" * ファイルに保存する小惑星の数 * "_"
* "p" / "m" (前方 / 後方積分) * sseph内の年数 * "y_et.jld2"
```

# 引数

  * `sseph::TaylorInterpolant`: すべての天体のエフェメリス。
  * `bodyind::T`: 保存する天体のインデックス。
  * `tspan::S`: 積分の時間範囲 (正 -> 前方積分 / 負 -> 後方積分)。

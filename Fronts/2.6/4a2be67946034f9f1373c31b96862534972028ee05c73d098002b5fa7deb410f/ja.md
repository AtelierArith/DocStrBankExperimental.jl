```
sorptivity(::InverseProblem)
```

半無限一次元非線形拡散問題の解の吸水性を計算します。解は離散点のセットとして与えられます。

数値積分を使用します。

# 引数

  * `prob::InverseProblem`: 逆問題。[`InverseProblem`](@ref)を参照してください。

# キーワード引数

  * `i=nothing`: 初期値。`nothing`の場合、初期値は`u[end]`から取得されます。
  * `b=nothing`: 境界値。`nothing`の場合、境界値は`u[begin]`から取得されます。
  * `ob=0`: 境界での`o`の値。

# 参考文献

PHILIP, J. R. The theory of infiltration: 4. Sorptivity and algebraic infiltration equations. Soil Science, 1957, vol. 83, no. 5, p. 345-357.

```
fig = marginplot(sys::LTISystem [,w::AbstractVector];  balance=true, kwargs...)
marginplot(sys::Vector{LTISystem}, w::AbstractVector;  balance=true, kwargs...)
```

システム `sys` のすべての振幅および位相余裕をプロットします。

  * 周波数ベクトル `w` をオプションで提供できます。
  * `balance`: プロットする前にシステムに対して [`balance_statespace`](@ref) を呼び出します。
  * `adjust_phase_start`: true の場合、位相は -90*intexcess 度から始まるように調整されます。ここで `intexcess` はシステムの積分器の余剰です。

`kwargs` は RecipesBase.plot への引数として送信されます。

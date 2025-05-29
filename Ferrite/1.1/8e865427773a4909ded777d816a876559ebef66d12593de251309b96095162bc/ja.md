```
function_value_jump(iv::InterfaceValues, q_point::Int, u)
function_value_jump(iv::InterfaceValues, q_point::Int, u, dof_range_here, dof_range_there)
```

インターフェース上の四分点での関数値のジャンプを計算します。デフォルトの法線方向に沿って。

この関数は定義 $\llbracket \vec{v} \rrbracket=\vec{v}^\text{there} -\vec{v}^\text{here}$ を使用します。形式 $\llbracket \vec{v} \rrbracket=\vec{v}^\text{there} ⋅ \vec{n}^\text{there} + \vec{v}^\text{here} ⋅ \vec{n}^\text{here}$ を得るために、インターフェースの最初の要素の側面に対して外向きの法線のマイナスを掛けます（これは [`getnormal`](@ref) と [`InterfaceValues`](@ref) のデフォルトの法線です）。

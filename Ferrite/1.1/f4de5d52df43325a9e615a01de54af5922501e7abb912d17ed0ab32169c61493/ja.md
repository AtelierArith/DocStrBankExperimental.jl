```
shape_gradient_jump(iv::InterfaceValues, qp::Int, i::Int)
```

形状関数 `i` の勾配のジャンプを、インターフェースを横切る四分点 `qp` で計算します。

この関数は定義 $\llbracket \vec{v} \rrbracket=\vec{v}^\text{there} -\vec{v}^\text{here}$ を使用します。形式 $\llbracket \vec{v} \rrbracket=\vec{v}^\text{there} ⋅ \vec{n}^\text{there} + \vec{v}^\text{here} ⋅ \vec{n}^\text{here}$ を得るために、インターフェースの最初の要素の側面に対する外向きの法線（これは [`getnormal`](@ref) と [`InterfaceValues`](@ref) のデフォルト法線です）に対してマイナスを掛けます。

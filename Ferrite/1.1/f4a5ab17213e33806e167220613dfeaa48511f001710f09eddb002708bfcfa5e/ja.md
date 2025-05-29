```
shape_value_jump(iv::InterfaceValues, qp::Int, i::Int)
```

インターフェースにおける四分点 `qp` での形状関数 `i` の値のジャンプを計算します。

この関数は定義 $\llbracket \vec{v} \rrbracket=\vec{v}^\text{there} -\vec{v}^\text{here}$ を使用します。形式 $\llbracket \vec{v} \rrbracket=\vec{v}^\text{there} \cdot \vec{n}^\text{there} + \vec{v}^\text{here} \cdot \vec{n}^\text{here}$ を得るために、インターフェースの最初の要素の側面に対する外向きの法線（これは [`getnormal`](@ref) と [`InterfaceValues`](@ref) のデフォルト法線です）に対してマイナスを掛けます。

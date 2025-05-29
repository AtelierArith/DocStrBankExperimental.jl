```
hnf_minors(A::MatrixElem{T}) where {T <: RingElement}
```

行列 $A$ の右上隅のエルミート正規形を Kannan-Bachem のアルゴリズムを使用して計算します。入力はフルカラムランクでなければなりません。

```
hnf_minors_with_transform(A::MatrixElem{T}) where {T <: RingElement}
```

行列 $A$ の上右行ヘルミート正規形 $H$ と $UA = H$ を満たす可逆行列 $U$ を、カンナン-バケムのアルゴリズムを用いて計算します。入力はフルカラムランクでなければなりません。

```
from_leave_incidence_matrix(lm::A, names, blv::Vector{<:AbstractFloat}) where A<:AbstractArray{<:Real, 2}
```

葉の発生行列を通じて指定された木を構築します。このパッケージの関数 $leave_incidence_matrix$ は、そのような行列を作成します。この関数は、再構築された木に割り当てられる枝の長さのベクトルも受け取ります。

行列から構築された木の根ノードを返します。

  * `lm` : 葉の発生行列
  * `names` : 葉の名前のリスト（行の順序で）
  * `blv` : この木に使用される枝の長さのベクトル

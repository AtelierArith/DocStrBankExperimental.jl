```
from_leave_incidence_matrix(lm::A, names) where A<:AbstractArray{<:Real, 2}
```

葉の発生行列を通じて指定された木を構築します。このパッケージの関数 $leave_incidence_matrix$ は、そのような行列を作成します。

行列から構築された木の根ノードを返します。

  * `lm` : 葉の発生行列
  * `names` : 葉の名前のリスト（行の順序で）

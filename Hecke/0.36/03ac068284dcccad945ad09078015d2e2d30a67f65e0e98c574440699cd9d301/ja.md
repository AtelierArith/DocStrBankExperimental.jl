```
hom(
  G::FinGenAbGroup,
  H::FinGenAbGroup,
  M::ZZMatrix,
  Minv::ZZMatrix;
  check::Bool=true,
) -> FinGenAbGroupHom
```

整数行列 $M = (m_{ij})$ によって定義される群準同型 $G\to H$ を返します（$G$ の $i$ 番目の生成元を $h_1,\ldots, h_n$ の生成元に対して $\sum_{j=1}^nm_{ij}h_j$ に送ります）。擬似逆行列 $H\to G$（または右逆行列）は `Minv` によって定義されます。`check` が `true` に設定されている場合、関数は $M$ と `Minv` が有限生成アーベル群の準同型を定義しているかどうか、また `Minv` が $M$ に対する右逆を定義しているかどうかをチェックします。

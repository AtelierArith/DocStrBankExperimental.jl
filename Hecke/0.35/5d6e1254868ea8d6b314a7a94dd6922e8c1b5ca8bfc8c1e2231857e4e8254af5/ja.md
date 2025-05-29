```
hom(
  G::FinGenAbGroup,
  H::FinGenAbGroup,
  M::ZZMatrix;
  check::Bool=true,
) -> FinGenAbGroupHom
```

整数行列 $M = (m_{ij})$ によって定義される群準同型 $G\to H$ を返します。これは、$G$ の $i$ 番目の生成元を $\sum_{j=1}^n m_{ij} h_j$ に送ります。ここで、$h_1,\ldots, h_n$ は $H$ の生成元です。`check` が `true` に設定されている場合、関数は `M` が有限生成アーベル群の準同型を定義しているかどうかをチェックします。

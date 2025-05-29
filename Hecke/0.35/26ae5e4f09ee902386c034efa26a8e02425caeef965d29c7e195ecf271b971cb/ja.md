```
hom(
  G::FinGenAbGroup,
  H::FinGenAbGroup,
  A::Vector,
  B::Vector;
  check::Bool=true,
) -> FinGenAbGroupHom
```

群準同型 $G\to H$ を返します。これはすべての $i$ に対して `A[i]` を `B[i]` に送ります。`check` が `true` に設定されている場合、関数は入力が有限生成アーベル群の準同型を定義しているかどうかを確認します。

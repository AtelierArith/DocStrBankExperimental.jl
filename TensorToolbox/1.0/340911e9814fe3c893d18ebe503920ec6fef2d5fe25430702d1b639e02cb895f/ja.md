```
trten2ten(B::Matrix,r1::Integer,r2::Integer)
trten2ten(B::MatrixCell,r1::Vector,r2::Vector)
```

テンソルをテンソルに転送します。転送テンソルが行列として与えられた場合、これを順序3およびサイズr1×r2×r3のテンソルに再形成します。ここで、`r3=size(B,2)`です。

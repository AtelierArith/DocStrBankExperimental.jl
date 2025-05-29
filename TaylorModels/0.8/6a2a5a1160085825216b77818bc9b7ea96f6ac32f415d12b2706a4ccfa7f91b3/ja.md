```markdown
bound_remainder(::Type{TaylorModel1}f::Function, polf::Taylor1, polfI::Taylor1, x0::Interval, I::Interval)

`f`のテイラー多項式`polf`によって与えられる多項式近似の絶対余剰を、区間`I`の`x0`の周りでバウンドします。これは、Lagrange余剰を計算するために、区間`I`全体の`f`を近似する多項式の区間拡張`polfI`を必要とします。

もし`polfI[end]`が明確な符号を持つ場合、これは区間[I.lo, x0]および[x0.hi, I.hi]で単調であるため、それを利用します。そうでない場合は、Lagrange余剰を計算するために使用されます。これは、Mioara Joldesの博士論文（pp 52）のProp 2.2.1に対応します。
```

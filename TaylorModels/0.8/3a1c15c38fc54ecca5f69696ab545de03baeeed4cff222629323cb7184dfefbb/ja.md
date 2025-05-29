```julia
bound_remainder(::Type{RTaylorModel1}, f::Function, polf::Taylor1, polfI::Taylor1, x0::Interval, I::Interval)

`f`のテイラー多項式`polf`によって与えられる多項式近似の相対余剰の上限を、区間`I`の`x0`の周りで求めます。これは、Lagrange余剰を計算するために、`I`全体の`f`を近似する多項式の区間拡張`polfI`が必要です。

`polfI[end]`が明確な符号を持つ場合、`I`の区間内で単調であるため、それを利用します。そうでない場合、最後の係数が相対余剰の上限を制約します。これは、Mioara Joldesの博士論文（pp 67）のProp 2.3.7に対応します。
```

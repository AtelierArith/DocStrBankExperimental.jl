```
qudits(n::Int; dim::Int = 3)
qudits(d⃗::Vector)
```

$$
n
$$

-quditヒルベルト空間を生成し、基底$\{\sigma_j\}_{j=1}^n$によって張られます。各局所自由度は、次元$d_j$を持つ`ITensors.Index`オブジェクトによって表されます。受け入れられる入力は、同じ局所次元$d$を持つquditの数、または局所次元のベクトル$\mathrm{d}=(d_1,\dots,d_n)$です。

```julia
q = qudits([3,5,3])
# 3-element Vector{ITensors.Index{Int64}}:
#  (dim=3|id=639|"Qudit,Site,n=1")
#  (dim=5|id=212|"Qudit,Site,n=2")
#  (dim=3|id=372|"Qudit,Site,n=3")
```

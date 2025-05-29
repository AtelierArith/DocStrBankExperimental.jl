```
qubits(n::Int)
```

$$
n
$$

-量子ビットのヒルベルト空間を生成し、基底$\{\sigma_j\}_{j=1}^n$によって張られます。各ローカル自由度は`ITensors.Index`オブジェクトによって表され、これはローカルヒルベルト空間の次元と自動テンソル収束のための一意の識別子をエンコードします。

```julia
q = qubits(3)
# 3-element Vector{ITensors.Index{Int64}}:
#  (dim=2|id=114|"Qubit,Site,n=1")
#  (dim=2|id=142|"Qubit,Site,n=2")
#  (dim=2|id=830|"Qubit,Site,n=3")
```

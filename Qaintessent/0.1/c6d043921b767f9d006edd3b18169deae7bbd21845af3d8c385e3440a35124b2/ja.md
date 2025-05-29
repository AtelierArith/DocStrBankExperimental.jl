```
unitary2circuit(m::Matrix{Complex64,2}) where {N}
```

は、与えられたユニタリ行列から量子回路をコンパイルします。ff10.1016/j.cpc.2019.107001f、10.1103/PhysRevA.69.032315、arxiv.org:1003.5760、arxiv:quant-ph/0404089からのアルゴリズムを実装しています。

# 例

```@example; setup = :(using RandomMatrices)
M = Stewart(ComplexF64, 4);
cgc = unitary2circuit(M)
```

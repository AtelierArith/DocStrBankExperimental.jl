# `random_edge`

行列ネットワークまたはスパース行列のランダムなエッジを特定します。

## 関数

  * `random_edge(A::MatrixNetwork) -> (ei,ej,ind)`   行列からランダムなエッジ/非ゼロを取得します
  * `random_edge(A::SparseMatrixCSC) -> (ei,ej,ind)`   行列からランダムな非ゼロを取得します

## 例

```
G = lollipop_graph(5,3)
# 地域間でランダムに見るエッジの数をカウントします
C = Dict{Symbol,Int}()
M = zeros(8,8)
for i=1:1000000
  ei,ej = MatrixNetwork.random_edge(G)
  M[ei,ej] += 1
  if 1 <= ei <= 5 && 1 <= ej <= 5
    C[:Stem] = get(C, :Stem, 0) + 1
  elseif 6 <= ei <= 10 && 6 <= ej <= 10
    C[:Pop] = get(C, :Pop, 0) + 1  
  else
    C[:Bridge] = get(C, :Bridge, 0) + 1  
  end
end
# ステムに4つのエッジ、ポップに3つのエッジ、ブリッジに1つのエッジ 
@show C
@show M
```

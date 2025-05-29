```
maximal_abelian_subfield(K::RelSimpleNumField{AbsSimpleNumFieldElem}; of_closure::Bool = false) -> ClassField
```

確率的アルゴリズムを使用してノルム群計算を行い、$K$の基底体に対する最大アーベル部分体を決定します。`of_closure`がtrueに設定されている場合、アルゴリズムは$K$の正規閉包に適用されます（計算は行いません）。

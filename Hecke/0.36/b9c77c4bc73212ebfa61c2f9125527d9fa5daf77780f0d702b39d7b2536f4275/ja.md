```
order(a::Vector{AbsSimpleNumFieldElem}; check::Bool = true, cached::Bool = true, isbasis::Bool = false) -> AbsSimpleNumFieldOrder
order(K::AbsSimpleNumField, a::Vector{AbsSimpleNumFieldElem}; check::Bool = true, cached::Bool = true, isbasis::Bool = false) -> AbsSimpleNumFieldOrder
```

$ a $ によって生成された順序を返します。`check` が設定されている場合、$ a $ が順序を定義するかどうかがチェックされ、特に要素の整数性は最小多項式を計算することによってチェックされます。`isbasis` が設定されている場合、要素は $\mathbf{Z}$-基底を形成するものと見なされます。`cached` が設定されている場合、構築された順序は将来の使用のためにキャッシュされます。

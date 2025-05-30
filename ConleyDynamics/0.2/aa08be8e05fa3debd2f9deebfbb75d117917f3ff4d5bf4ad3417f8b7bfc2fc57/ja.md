```
lefschetz_reduction(lc::LefschetzComplex, redpairs::Vector{Vector{Int}})
```

Lefschetz複体に対して一連の基本的な削減を適用します。

削減ペアは引数`redpairs`で指定する必要があります。各エントリは、インデックス形式の基本的な削減ペアを含む長さ2のベクトルでなければなりません。特に、ペア内の2つのセルの次元は1だけ異なり、削減の順序でペアに到達したとき、一方のセルは他方のセルの面でなければなりません。この関数は、`redpairs`内のすべてのセルが削除された新しいLefschetz複体を返します。

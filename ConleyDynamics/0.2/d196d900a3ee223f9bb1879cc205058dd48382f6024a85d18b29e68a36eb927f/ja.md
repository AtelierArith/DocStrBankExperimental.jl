```
lefschetz_reduction(lc::LefschetzComplex, redpairs::Vector{Vector{String}})
```

Lefschetz複体に対して一連の基本的な削減を適用します。

削減ペアは引数`redpairs`で指定する必要があります。各エントリは長さ2のベクトルであり、基本的な削減ペアをラベル形式で含む必要があります。特に、ペア内の2つのセルの次元は1だけ異なる必要があり、削減の順序でペアに到達したとき、一方のセルは他方の面でなければなりません。この関数は、`redpairs`内のすべてのセルが削除された新しいLefschetz複体を返します。

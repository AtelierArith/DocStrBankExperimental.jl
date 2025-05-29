欠損値を埋めるために線形補間を使用します。この関数は、夜間の光放射時系列データだけでなく、あらゆる種類の配列に対して機能します。

```
x = rand(1:10.0, 10)
x = Vector{Union{Missing, Float64}}(x)
x[5] = missing
na_interp_linear(x)
```

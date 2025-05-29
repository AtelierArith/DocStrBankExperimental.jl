```
dmatrix_flatten(dmatrix::Array{Float64,3}, flatten::Any)
```

文字列 "flatten" で指定された方法を使用して dmatrix をフラット化します。

### 入力引数

  * `dmatrix::Array{Float64,3}`: 拡張係数の行列; この関数が呼び出された後、サイズは (~, ~, 1) になります。
  * `flatten::Any`: dmatrix をフラット化するための方法 (詳細はコードを参照)

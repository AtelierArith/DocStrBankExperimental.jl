```
minor_axis(matrix::AbstractMatrix)::Maybe{Int8}
```

行列のマイナー軸のインデックスを返します。つまり、行列要素に効率的にアクセスするために**変化させる**べき軸です。行列が効率的なアクセス軸をサポートしていない場合は、`nothing`を返します。

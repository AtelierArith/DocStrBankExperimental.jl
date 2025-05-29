```
isrotation(r)
isrotation(r, tol)
```

`r`が回転行列であるかどうかを確認します。ここで、`r * r'`が単位行列に対して`tol`以内であることを確認します（フロベニウスノルムを使用）。`tol`のデフォルト値は`1000 * eps(float(eltype(r)))`または整数`T`の場合は`zero(T)`です。

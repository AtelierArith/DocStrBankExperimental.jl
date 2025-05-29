```
Forcing(array::AbstractArray)
```

`array`によって`Forcing`を返します。これはモデルフィールドの傾向に追加できます。

Forcingは`array[i, j, k]`を呼び出すことによって計算されるため、`array`は`size(grid)`を持つ3Dでなければなりません。

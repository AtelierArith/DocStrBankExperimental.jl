```
lift(M::smodule{T}, SM::smodule{T}) where T
```

`SM`の生成子を`M`の生成子の観点から表します。もし`SM`が`M`に含まれる場合、`rest`は零モジュールであり、そうでない場合は`rest = reduce(SM, std(M))`となります。グローバル順序の場合、`(result, rest)`を返します：`Matrix(SM) - Matrix(rest) = Matrix(M)*Matrix(result)` 非グローバル順序の場合：`Matrix(SM)*U - Matrix(rest) = Matrix(M)*Matrix(result)` ここで`U`は単位の対角行列です。この`U`を計算するには、`lift(M::smodule, SM::smodule, goodShape::Bool, isSB::Bool, divide::Bool)`を参照してください。

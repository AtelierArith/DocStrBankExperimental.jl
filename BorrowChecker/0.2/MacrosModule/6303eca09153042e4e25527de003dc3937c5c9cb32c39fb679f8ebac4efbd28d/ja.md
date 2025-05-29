```
@ref ~lifetime [:mut] var = value
@ref ~lifetime [:mut] (var1, var2, ...) = (value1, value2, ...)
@ref ~lifetime [:mut] for var in iter
    # body
end
```

所有値への参照をライフタイムスコープ内で作成します。ライフタイムスコープの詳細については、`@lifetime`マクロを参照してください。

`:mut`が指定されている場合、可変参照を作成します。そうでない場合は、不変参照を作成します。基になる値へのアクセスを転送するBorrowed{T}またはBorrowedMut{T}を返します。

!!! warning
    これはイテレータ内のエイリアシングを検出しません。


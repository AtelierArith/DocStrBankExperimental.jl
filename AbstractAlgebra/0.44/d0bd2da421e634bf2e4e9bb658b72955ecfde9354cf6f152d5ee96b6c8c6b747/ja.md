```
inv!(z, a)
inv!(a)
```

`AbstractAlgebra.inv(a)`を返します。プロセス中にオブジェクト`z`を変更する可能性があります。エイリアスを許可します。単項バージョンは`inv!(a, a)`の短縮形です。

!!! note
    `AbstractAlgebra.inv`と`Base.inv`は、`Integer`や`Rational{Int}`のようなjuliaタイプに対する動作のみが異なります。前者はリングインターフェースに従うようにします。


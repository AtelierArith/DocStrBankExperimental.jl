```
div!(z, a, b)
div!(a, b)
```

`div(a, b)`を返しますが、その過程でオブジェクト`z`を変更する可能性があります。エイリアスは許可されています。2つの引数のバージョンは`div(a, a, b)`の短縮形です。

!!! note
    `AbstractAlgebra.div`と`Base.div`は、`Integer`や`Rational{Int}`のようなjulia型に対する動作のみが異なります。前者はリングインターフェースに従うようにします。


```
object = revert(transform, newobject, cache)
```

`newobject`に対して`cache`を使用して対応する[`apply`](@ref)呼び出しから`transform`を元に戻し、元の`object`を返します。`transform`が[`isrevertible`](@ref)である場合にのみ定義されています。

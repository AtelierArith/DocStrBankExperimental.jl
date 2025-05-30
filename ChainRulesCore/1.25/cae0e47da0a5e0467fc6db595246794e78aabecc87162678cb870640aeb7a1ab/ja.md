```
InplaceableThunk(add!::Function, val::Thunk)
```

`Thunk`のラッパーで、インプレースの`add!`関数を定義できるようにします。

`add!`は次のように定義されるべきです: `ithunk.add!(Δ) = Δ .+= ithunk.val` しかし、これを直接行うよりも効率的に行う必要があります。（そうでなければ、通常の`Thunk`を使えばよいのです）。

`InplaceableThunk`に対するほとんどの操作は、それを通常の`Thunk`のように扱い、そのインプレース性を破壊します。

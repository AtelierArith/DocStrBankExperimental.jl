```
setinverse(f, invf)
```

`f`のように振る舞い、`invf`をその逆関数として使用する関数を返します。

`f`に対して逆関数が定義されていない場合や、特定の文脈内でのみ有効な逆関数を設定する場合に便利です。たとえば、使用ケースによって保証される限られた引数範囲内でのみ有効です。

たとえば、`asin`は任意の`sin`の引数に対して有効な逆関数ではありませんが、`sin`の引数が常に`-π`と`π`の範囲内であることが保証される場合には有効な逆関数となります：

```jldoctest
julia> foo = setinverse(sin, asin);

julia> x = π/3;

julia> foo(x) == sin(x)
true

julia> inverse(foo)(foo(x)) ≈ x
true

julia> inverse(foo) === setinverse(asin, sin)
true
```

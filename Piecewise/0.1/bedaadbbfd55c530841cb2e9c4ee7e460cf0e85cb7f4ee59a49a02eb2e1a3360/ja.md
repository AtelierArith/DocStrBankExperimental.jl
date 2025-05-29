```
format(f::PiecewiseFunction)
```

`PiecewiseFunction`オブジェクト`f`のコンストラクタを保持する文字列を返します。名前を持つ[`Formula`](@ref)オブジェクトの場合、`Formula`オブジェクトのコンストラクタの代わりに名前が使用されます。`print(f)`は`print(format(f))`と同等であることに注意してください。

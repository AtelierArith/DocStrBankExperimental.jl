```
reconstruct(pp; kws...
reconstruct(T::Type, pp; kws...)
```

入力タイプと同じ値を持つ新しいインスタンスを作成しますが、キーワード引数で指定されたフィールドは除きます。タイプ、Dict、およびNamedTuplesに対して機能します。また、再構築時にパラメータが変更されるパラメータ化されたタイプに対して、別のタイプに再構築することもできます。

注意: これは非常にパフォーマンスが良くありません。より高速で素敵な実装についてはSetfield.jlを確認してください。

```jldoctest
julia> using Parameters

julia> struct A
           a
           b
       end

julia> x = A(3,4)
A(3, 4)

julia> reconstruct(x, b=99)
A(3, 99)

julia> struct B{T}
          a::T
          b
       end

julia> y = B(sin, 1)
B{typeof(sin)}(sin, 1)

julia> reconstruct(B, y, a=cos) # note reconstruct(y, a=cos) errors!
B{typeof(cos)}(cos, 1)
```

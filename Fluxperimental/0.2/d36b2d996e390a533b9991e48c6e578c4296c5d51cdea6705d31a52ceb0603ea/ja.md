```
@autostruct MyType(field1, field2, ...)
```

このように `function` なしで使用すると、マクロは指定されたフィールドを持つ `struct` を作成します。 `@autostruct MyType(field1, field2::Function)` は大体次のように展開されます：

```julia
struct MyType003{T1, T2 <: Function}
  field1::T1
  fiedl2::T2
end

Flux.@layer :expand MyType002

MyType = MyType003  # これにより再定義が可能になります
```

これを Flux レイヤーとして使用するには、例えば次のように呼び出し可能にする必要があります：

```julia
(m::MyType)(x) = m.field1(x) .+ x .|> m.field2

m1 = MyType(Chain(vcat, Dense(1 => 5, relu)), cbrt)

m1(-2)
```

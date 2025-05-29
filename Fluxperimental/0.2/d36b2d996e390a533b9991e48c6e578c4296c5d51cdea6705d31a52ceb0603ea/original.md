```
@autostruct MyType(field1, field2, ...)
```

Used like this, without a `function`, the macro creates a `struct` with the fields indicated. `@autostruct MyType(field1, field2::Function)` expands to roughly this:

```julia
struct MyType003{T1, T2 <: Function}
  field1::T1
  fiedl2::T2
end

Flux.@layer :expand MyType002

MyType = MyType003  # this allows re-definition
```

To use this as a Flux layer, you will also need to make it callable, by writing for instance:

```julia
(m::MyType)(x) = m.field1(x) .+ x .|> m.field2

m1 = MyType(Chain(vcat, Dense(1 => 5, relu)), cbrt)

m1(-2)
```

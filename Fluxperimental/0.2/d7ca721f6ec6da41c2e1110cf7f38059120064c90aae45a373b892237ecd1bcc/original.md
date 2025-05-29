```
@autostruct function MyLayer(d); ...; MyLayer(f1, f2, ...); end
```

This is a macro for easily defining new layers.

Recall that Flux layer is a callable `struct` which may contain parameter arrays. Usually, the steps to define a new one are:

1. Define a `struct MyLayer` with the desired fields, and tell Flux to look inside with `@layer MyLayer` (or on earlier versions, `@functor`).
2. Define a constructor function like `MyLayer(d::Int)`, which initialises the parameters (say to `randn32(d, d)`) and returns an instance of the `struct`, some `m::MyLayer`.
3. Define the forward pass, by making the struct callable: `(m::MyLayer)(x) = ...`

Given the function in step 2, this macro handles step 1. You still do step 3.

If you change the name or types of the fields, then the `struct` definition is automatically replaced, without re-starting Julia. This works because this definition uses an auto-generated name, which is `== MyLayer`. (But existing instances of the old `struct` are not changed in any way!)

Writing `@autostruct :expand function MyLayer(d)` will use `@layer :expand MyLayer`, and result in container-style pretty-printing.

See [AutoStructs.jl](https://github.com/CarloLucibello/AutoStructs.jl) for a version of this macro aimed at non-Flux uses.

## Examples

```julia
@autostruct function MyModel(d::Int)
  alpha, beta = [Dense(d=>d, tanh) for _ in 1:2]    # arbitrary code here, not just keyword-like
  beta.bias[:] .= 1/d
  return MyModel(alpha, beta)  # this must be very simple, no = signs allowed (return optional)
end

function (m::MyModel)(x)  # forward pass looks just like a normal struct
  y = m.alpha(x)
  z = m.beta(y)
  (x .+ y .+ z)./3
end

Flux.trainable(m::MyModel) = (; m.alpha)  # if necessary, restrict which fields are trainable

Base.show(io::IO, m::MyModel) =  # if desired, replace default printing "MyModel(...)"
  print(io, "MyModel(", size(m.alpha.weight, 1), ")")

MyModel(2) isa MyModel  # true
```

The `struct` defined by the macro here is something like this:

```julia
struct MyModel001{T1, T2}
  alpha::T1
  beta::T2
end
```

This can hold any objects, even `MyModel("hello", "world")`. As you can see by looking `methods(MyModel)`, there should never be an ambiguity between the `struct`'s own constructor, and your `MyModel(d::Int)`.

You can also restrict the types allowed in the struct:

```
@autostruct :expand function MyOtherModel(d1, d2, act=identity)
  gamma = Embedding(128 => d1)
  delta = Dense(d1 => d2, act)
  MyOtherModel(gamma::Embedding, delta::Dense)  # struct will only hold these types
end

(m::MyOtherModel)(x) = softmax(m.delta(m.gamma(x)))  # forward pass

methods(MyOtherModel)  # will show 3 methods
```

Such restrictions change the struct like this:

```julia
struct MyOtherModel002{T1 <: Embedding, T2 <: Dense}
  gamma::T1
  delta::T2
end
```

If you need to add additional constructor methods, the obvious syntax will not work. But you can add them to the type, like this:

```julia
MyModel(str::String) = MyModel(parse(Int, str))
# ERROR: cannot define function MyModel; it already has a value

(::Type{MyModel})(str::String) = MyModel(parse(Int, str))
MyModel("4")  # this works
```

## Compared to `@compact`

For comparison, the use of `@compact` to do much the same thing looks like this – shorter, but further from being ordinary Julia code.

```julia
function MyModel2(d::Int)
    alpha, beta = [Dense(d=>d, tanh) for _ in 1:2]
    beta.bias[:] .= 1/d
    @compact(; alpha, beta) do x
        y = alpha(x)
        z = beta(y)
        (x .+ y .+ z)./3
    end
end

MyModel2(2) isa Fluxperimental.CompactLayer  # no easy struct type

MyOtherModel2(d1, d2, act=identity) =
  @compact(gamma = Embedding(128 => d1), delta=Dense(d1 => d2, act)) do x
    softmax(delta(gamma(x)))
  end
```

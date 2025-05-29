```
@check [key=val]... function...
```

The main way to declare & run a property based test. Called like so:

```julia-repl
julia> using Supposition, Supposition.Data

julia> Supposition.@check [options...] function foo(a = Data.Text(Data.Characters(); max_len=10))
          length(a) > 8
       end
```

Supported options, passed as `key=value`:

  * `rng::Random.AbstractRNG`: Pass an RNG to use. Defaults to `Random.Xoshiro(rand(Random.RandomDevice(), UInt))`.
  * `max_examples::Int`: The maximum number of generated examples that are passed to the property.
  * `broken::Bool`: Mark a property that should pass but doesn't as broken, so that failures are not counted.
  * `record::Bool`: Whether the result of the invocation should be recorded with any parent testsets.
  * `db`: Either a Boolean (`true` uses a fallback database, `false` stops recording examples) or an [`ExampleDB`](@ref).
  * `config`: A `CheckConfig` object that will be used as a default for all previous options. Options that are passed explicitly to `@check` will override whatever is provided through `config`.

The arguments to the given function are expected to be generator strategies. The names they are bound to are the names the generated object will have in the test. These arguments will be shown should the property fail!

# Extended help

## Reusing existing properties

If you already have a predicate defined, you can also use the calling syntax in `@check`. Here, the generator is passed purely positionally to the given function; no argument name is necessary.

```julia-repl
julia> using Supposition, Supposition.Data

julia> isuint8(x) = x isa UInt8

julia> intgen = Data.Integers{UInt8}()

julia> Supposition.@check isuint8(intgen)
```

## Passing a custom RNG

It is possible to optionally give a custom RNG object that will be used for random data generation. If none is given, `Xoshiro(rand(Random.RandomDevice(), UInt))` is used instead.

```julia-repl
julia> using Supposition, Supposition.Data, Random

# use a custom Xoshiro instance
julia> Supposition.@check rng=Xoshiro(1234) function foo(a = Data.Text(Data.Characters(); max_len=10))
          length(a) > 8
       end
```

!!! warning "Hardware RNG"
    Be aware that you *cannot* pass a hardware RNG to `@check` directly. If you want to randomize based on hardware entropy, seed a copyable RNG like `Xoshiro` from your hardware RNG and pass that to `@check` instead. The RNG needs to be copyable for reproducibility.


## Additional Syntax

In addition to passing a whole `function` like above, the following syntax are also supported:

```julia
text = Data.Text(Data.AsciiCharacters(); max_len=10)

# If no name is needed, use an anonymous function
@check (a = text) -> a*a
@check (a = text,) -> "foo: "*a
@check (a = text, num = Data.Integers(0,10)) -> a^num

# ..or give the anonymous function a name too - works with all three of the above
@check build_sentence(a = text, num = Data.Floats{Float16}()) -> "The $a is $num!"
build_sentence("foo", 0.5) # returns "The foo is 0.5!"
```

!!! warning "Replayability"
    While you can pass an anonymous function to `@check`, be aware that doing so may hinder replayability of found test cases when surrounding invocations of `@check` are moved. Only named functions are resistant to this.


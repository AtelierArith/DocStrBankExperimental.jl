```
@composed
```

A way to compose multiple `Possibility` into one, by applying a function.

The return type is inferred as a best-effort!

Used like so:

```julia-repl
julia> using Supposition, Supposition.Data

julia> text = Data.Text(Data.AsciiCharacters(); max_len=10)

julia> gen = Supposition.@composed function foo(a = text, num=Data.Integers(0, 10))
              lpad(num, 2) * ": " * a
       end

julia> example(gen)
" 8:  giR2YL\rl"
```

In addition to passing a whole `function` like above, the following syntax are also supported:

```julia
# If no name is needed, use an anonymous function
double_up =  @composed (a = text) -> a*a
prepend_foo = @composed (a = text,) -> "foo: "*a
expo_str = @composed (a = text, num = Data.Integers(0,10)) -> a^num

# ..or give the anonymous function a name too - works with all three of the above
sentence = @composed build_sentence(a = text, num = Data.Floats{Float16}()) -> "The $a is $num!"
build_sentence("foo", 0.5) # returns "The foo is 0.5!"

# or compose a new generator out of an existing function
my_func(str, number) = number * "? " * str
ask_number = @composed my_func(text, num)
```

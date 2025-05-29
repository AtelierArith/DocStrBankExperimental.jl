```
RE(s::AbstractString)
```

Automa regular expression (regex) that is used to match a sequence of input bytes. Regex should preferentially be constructed using the `@re_str` macro: `re"ab+c?"`. Regex can be combined with other regex, strings or chars with `*`, `|`, `&` and `\`:

  * `a * b` matches inputs that matches first `a`, then `b`
  * `a | b` matches inputs that matches `a` or `b`
  * `a & b` matches inputs that matches `a` and `b`
  * `a \ b` matches input that mathes `a` but not `b`
  * `!a` matches all inputs that does not match `a`.

Set actions to regex with [`onenter!`](@ref), [`onexit!`](@ref), [`onall!`](@ref) and [`onfinal!`](@ref), and preconditions with [`precond!`](@ref).

# Example

```julia
julia> regex = (re"a*b?" | opt('c')) * re"[a-z]+";

julia> regex = rep1((regex \ "aba") & !re"ca");

julia> regex isa RE
true

julia> compile(regex) isa Automa.Machine
true
```

See also: [`@re_str`](@ref), [`compile`](@ref Main.Automa.compile)

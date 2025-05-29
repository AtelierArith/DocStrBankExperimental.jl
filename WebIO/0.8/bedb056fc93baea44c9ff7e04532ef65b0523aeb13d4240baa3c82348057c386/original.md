```
@js_str(s)
```

Create a `JSString` using a string literal and perform interpolations from Julia.

# Examples

```julia-repl
julia> mystr = "foo"; mydict = Dict("foo" => "bar", "spam" => "eggs");
julia> println(js"const myStr = $mystr; const myObject = $mydict;")
const myStr = "foo"; const myObject = {"spam":"eggs","foo":"bar"};
```

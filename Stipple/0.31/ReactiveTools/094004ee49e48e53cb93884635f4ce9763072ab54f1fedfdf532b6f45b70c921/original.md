```
@methods(expr)
@methods(App, expr)
```

Defines js functions for the `methods` section of the vue element.

`expr` can be

  * `String` containing javascript code
  * `Pair` of function name and function code
  * `Function` returning String of javascript code
  * `Dict` of function names and function code
  * `Vector` of the above

### Example 1

```julia
@methods "greet: function(name) {console.log('Hello ' + name)}"
```

### Example 2

```julia
js_greet() = :greet => "function(name) {console.log('Hello ' + name)}"
js_bye() = :bye => "function() {console.log('Bye!')}"
@methods MyApp [js_greet, js_bye]
```

Checking the result can be done in the following way

```
julia> render(MyApp())[:methods].s |> println
{
    "greet":function(name) {console.log('Hello ' + name)},
    "bye":function() {console.log('Bye!')}
}
```

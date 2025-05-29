```
@computed(expr)
@computed(App, expr)
```

Defines js functions for the `computed` section of the vue element.

`expr` can be

  * `String` containing javascript code
  * `Pair` of function name and function code
  * `Function` returning String of javascript code
  * `Dict` of function names and function code
  * `Vector` of the above

### Example 1

```julia
@computed "greet: function(name) {console.log('Hello ' + name)}"
```

### Example 2

```julia
js_greet() = :greet => "function(name) {console.log('Hello ' + name)}"
js_bye() = :bye => "function() {console.log('Bye!')}"
@computed MyApp [js_greet, js_bye]
```

Checking the result can be done in the following way

```
julia> render(MyApp())[:computed].s |> println
{
    "greet":function(name) {console.log('Hello ' + name)},
    "bye":function() {console.log('Bye!')}
}
```

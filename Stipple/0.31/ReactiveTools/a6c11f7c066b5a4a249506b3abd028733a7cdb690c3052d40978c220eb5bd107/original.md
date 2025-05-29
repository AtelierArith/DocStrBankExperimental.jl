```
@before_update(expr)
```

Defines js statements for the `beforeUpdate` section of the vue element.

expr can be

  * `String` containing javascript code
  * `Function` returning String of javascript code
  * `Vector` of the above

### Example 1

```julia
@before_update """
    if (this.cameraon) { startcamera() }
"""
```

### Example 2

```julia
startcamera() = "if (this.cameraon) { startcamera() }"
stopcamera() = "if (this.cameraon) { stopcamera() }"

@before_update MyApp [startcamera, stopcamera]
```

Checking the result can be done in the following way

```
julia> render(MyApp())[:beforeUpdate]
JSONText("function(){
    if (this.cameraon) { startcamera() }

    if (this.cameraon) { stopcamera() }
}")
```

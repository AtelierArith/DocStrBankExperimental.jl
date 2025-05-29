```
@error_captured(expr)
```

Defines js statements for the `errorCaptured` section of the vue element.

expr can be

  * `String` containing javascript code
  * `Function` returning String of javascript code
  * `Vector` of the above

### Example 1

```julia
@error_captured """
    if (this.cameraon) { startcamera() }
"""
```

### Example 2

```julia
startcamera() = "if (this.cameraon) { startcamera() }"
stopcamera() = "if (this.cameraon) { stopcamera() }"

@error_captured MyApp [startcamera, stopcamera]
```

Checking the result can be done in the following way

```
julia> render(MyApp())[:errorCaptured]
JSONText("function(){
    if (this.cameraon) { startcamera() }

    if (this.cameraon) { stopcamera() }
}")
```

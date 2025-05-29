```julia
@onbutton
```

Declares a reactive update that executes `expr` when a button is pressed in the UI.

**Usage** Define a click event listener with `@click`, and the handler with `@onbutton`.

```julia
@app begin
    @in press = false
    @onbutton press begin
        println("Button presed!")
    end
end

ui() = btn("Press me", @click(:press))

@page("/", ui)
```

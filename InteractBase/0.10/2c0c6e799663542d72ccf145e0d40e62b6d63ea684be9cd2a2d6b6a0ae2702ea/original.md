`confirm([f,] text="")`

Creates a `Widget{:confirm}`. To cause it to trigger a confirmation dialogue, do:

```julia
wdg = confirm([f,] "Are you sure you want to unsubscribe?")
wdg()
```

`observe(wdg)` is a `Observable{Bool}` and is set to `true` if the user clicks on "OK" in the dialogue, or to false if the user closes the dialogue or clicks on "Cancel". When `observe(wdg)` is set, the function `f` will be called with that value.

Calling `wdg` with a string and/or a function will set the confirmation message and/or the callback function:

```julia
wdg = confirm("Are you sure you want to unsubscribe?")
wdg("File exists, overwrite?") do x
   x ? print("Overwriting") : print("Aborting")
end
```

For the javascript to work, the widget needs to be part of the UI, even though it is not visible.

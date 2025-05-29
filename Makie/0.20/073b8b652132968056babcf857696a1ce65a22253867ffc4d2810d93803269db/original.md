```
Exclusively(x)
```

Marks a button, button collection or logical expression of buttons as the exclusive subset of buttons that must be pressed for `ispressed` to return true.

For example `Exclusively((Keyboard.left_control, Keyboard.c))` would require left control and c to be pressed without any other buttons.

Boolean expressions are lowered to multiple `Exclusive` sets in an `Or`. It is worth noting that `Not` branches are ignored here, i.e. it assumed that every button under a `Not` must not be pressed and that this follows automatically from the subset of buttons that must be pressed.

See also: [`And`](@ref), [`Or`](@ref), [`Not`](@ref), [`ispressed`](@ref), [`&`](@ref), [`|`](@ref), [`!`](@ref)

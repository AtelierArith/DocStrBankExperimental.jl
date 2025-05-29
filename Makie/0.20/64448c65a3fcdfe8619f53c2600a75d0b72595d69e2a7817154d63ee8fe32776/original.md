ispressed(parent, result::Bool[, waspressed = nothing]) ispressed(parent, button::Union{Mouse.Button, Keyboard.Button[, waspressed = nothing])     ispressed(parent, collection::Union{Set, Vector, Tuple}[, waspressed = nothing])     ispressed(parent, op::BooleanOperator[, waspressed = nothing])

This function checks if a button or combination of buttons is pressed.

If given a true or false, `ispressed` will return true or false respectively. This provides a way to turn an interaction "always on" or "always off" from the outside.

Passing a button or collection of buttons such as `Keyboard.enter` or `Mouse.left` will return true if all of the given buttons are pressed.

Parent can be any object that has `get_scene` method implemented, which includes e.g. Figure, Axis, Axis3, Lscene, FigureAxisPlot, and AxisPlot.

For more complicated combinations of buttons they can be combined into boolean expression with `&`, `|` and `!`. For example, you can have `ispressed(parent, !Keyboard.left_control & Keyboard.c))` and `ispressed(parent, Keyboard.left_control & Keyboard.c)` to avoid triggering both cases at the same time.

Furthermore you can also make any button, button collection or boolean expression exclusive by wrapping it in `Exclusively(...)`. With that `ispressed` will only return true if the currently pressed buttons match the request exactly.

For cases where you want to react to a release event you can optionally add a key or mousebutton `waspressed` which is then assumed to be pressed regardless of it's current state. For example, when reacting to a mousebutton event, you can pass `event.button` so that a key combination including that button still evaluates as true.

See also: [`waspressed`](@ref) [`And`](@ref), [`Or`](@ref), [`Not`](@ref), [`Exclusively`](@ref), [`&`](@ref), [`|`](@ref), [`!`](@ref)

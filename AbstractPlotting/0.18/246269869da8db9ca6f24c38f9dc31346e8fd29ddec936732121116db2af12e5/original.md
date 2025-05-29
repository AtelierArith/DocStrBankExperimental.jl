This struct provides accessible `PriorityObservable`s to monitor the events associated with a Scene.

Functions that act on a `PriorityObservable` must return true if the function  consumes an event and false if it does not. When an event is consumed it does  not trigger other observer functions. The order in which functions are exectued can be controlled via the `priority` keyword (default 0) in `on`.

Example:

```
on(events(scene).mousebutton, priority = Int8(20)) do event
    if is_correct_event(event)
        do_something()
        return true
    end
    return false
end
```

## Fields

  * `window_area::AbstractPlotting.PriorityObservable{GeometryBasics.HyperRectangle{2, Int64}}`: The area of the window in pixels, as a `Rect2D`.

  * `window_dpi::AbstractPlotting.PriorityObservable{Float64}`: The DPI resolution of the window, as a `Float64`.

  * `window_open::AbstractPlotting.PriorityObservable{Bool}`: The state of the window (open => true, closed => false).

  * `mousebutton::AbstractPlotting.PriorityObservable{AbstractPlotting.MouseButtonEvent}`: Most recently triggered `MouseButtonEvent`. Contains the relevant `event.button` and `event.action` (press/release)

    See also [`ispressed`](@ref).

  * `mousebuttonstate::Set{AbstractPlotting.Mouse.Button}`: A Set of all currently pressed mousebuttons.

  * `mouseposition::AbstractPlotting.PriorityObservable{Tuple{Float64, Float64}}`: The position of the mouse as a `NTuple{2, Float64}`. Updates once per event poll/frame.

  * `scroll::AbstractPlotting.PriorityObservable{Tuple{Float64, Float64}}`: The direction of scroll

  * `keyboardbutton::AbstractPlotting.PriorityObservable{AbstractPlotting.KeyEvent}`: Most recently triggered `KeyEvent`. Contains the relevant `event.key` and `event.action` (press/repeat/release)

    See also [`ispressed`](@ref).

  * `keyboardstate::Set{AbstractPlotting.Keyboard.Button}`: Contains all currently pressed keys.

  * `unicode_input::AbstractPlotting.PriorityObservable{Char}`: Contains the last typed character.

  * `dropped_files::AbstractPlotting.PriorityObservable{Vector{String}}`: Contains a list of filepaths to files dragged into the scene.

  * `hasfocus::AbstractPlotting.PriorityObservable{Bool}`: Whether the Scene window is in focus or not.

  * `entered_window::AbstractPlotting.PriorityObservable{Bool}`: Whether the mouse is inside the window or not.

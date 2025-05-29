This struct provides accessible `Observable`s to monitor the events associated with a Scene.

Functions that act on an `Observable` must return `Consume()` if the function consumes an event. When an event is consumed it does not trigger other observer functions. The order in which functions are executed can be controlled via the `priority` keyword (default 0) in `on`.

Example:

```julia
on(events(scene).mousebutton, priority = 20) do event
    if is_correct_event(event)
        do_something()
        return Consume()
    end
    return
end
```

## Fields

  * `window_area::Observables.Observable{GeometryBasics.HyperRectangle{2, Int64}}`: The area of the window in pixels, as a `Rect2`.

  * `window_dpi::Observables.Observable{Float64}`: The DPI resolution of the window, as a `Float64`.

  * `window_open::Observables.Observable{Bool}`: The state of the window (open => true, closed => false).

  * `mousebutton::Observables.Observable{Makie.MouseButtonEvent}`: Most recently triggered `MouseButtonEvent`. Contains the relevant `event.button` and `event.action` (press/release)

    See also [`ispressed`](@ref).

  * `mousebuttonstate::Set{Makie.Mouse.Button}`: A Set of all currently pressed mousebuttons.

  * `mouseposition::Observables.Observable{Tuple{Float64, Float64}}`: The position of the mouse as a `NTuple{2, Float64}`. Updates once per event poll/frame.

  * `scroll::Observables.Observable{Tuple{Float64, Float64}}`: The direction of scroll

  * `keyboardbutton::Observables.Observable{Makie.KeyEvent}`: Most recently triggered `KeyEvent`. Contains the relevant `event.key` and `event.action` (press/repeat/release)

    See also [`ispressed`](@ref).

  * `keyboardstate::Set{Makie.Keyboard.Button}`: Contains all currently pressed keys.

  * `unicode_input::Observables.Observable{Char}`: Contains the last typed character.

  * `dropped_files::Observables.Observable{Vector{String}}`: Contains a list of filepaths to files dragged into the scene.

  * `hasfocus::Observables.Observable{Bool}`: Whether the Scene window is in focus or not.

  * `entered_window::Observables.Observable{Bool}`: Whether the mouse is inside the window or not.

  * `tick::Observables.Observable{Makie.Tick}`: A `tick` is triggered whenever a new frame is requested, i.e. during normal rendering (even if the renderloop is paused) or when an image is produced for `save` or `record`. A Tick contains:

      * `state` which identifies what caused the tick (see Makie.TickState)
      * `count` which increments with every tick
      * `time` which is the total time since the screen has been created
      * `delta_time` which is the time since the last frame

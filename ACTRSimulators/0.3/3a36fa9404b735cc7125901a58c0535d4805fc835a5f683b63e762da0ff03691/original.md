*AbstractTask*

An abstract type for a task. A task requires the following fields:

  * `visible`: shows GUI if true
  * `realtime`: executes model in realtime if true
  * `speed`: speed of realtime model execution
  * `scheduler`: a reference to the event scheduler

A task may optionally contain the following fields:

  * `screen`: a vector of visual objects on the screen
  * `canvas`: a GUI object component
  * `window`: a window for the GUI

*Example*

The following is an example of the task object for the PVT.

```julia
mutable struct PVT{T,W,C,F1,F2} <: AbstractTask 
    n_trials::Int
    trial::Int 
    lb::Float64
    ub::Float64 
    width::Float64
    hight::Float64
    scheduler::T
    screen::Vector{VisualObject}
    canvas::C
    window::W
    visible::Bool
    realtime::Bool
    speed::Float64
end    
```

The constructor for `PVT` is 

```julia
function PVT(;
    n_trials=10, 
    trial=1, 
    lb=2.0, 
    ub=10.0, 
    width=600.0, 
    height=600.0, 
    scheduler=nothing, 
    screen=Vector{VisualObject}(), 
    window=nothing, 
    canvas=nothing, 
    visible=false, 
    realtime=false,
    speed=1.0,
    )
    visible ? ((canvas,window) = setup_window(width)) : nothing
    visible ? Gtk.showall(window) : nothing
    return PVT(n_trials, trial, lb, ub, width, height, scheduler, screen, canvas, window, visible,
        realtime, speed)
end

function setup_window(width)
	canvas = @GtkCanvas()
    window = GtkWindow(canvas, "PVT", width, width)
    Gtk.visible(window, true)
    @guarded draw(canvas) do widget
        ctx = getgc(canvas)
        rectangle(ctx, 0.0, 0.0, width, width)
        set_source_rgb(ctx, .8, .8, .8)
        fill(ctx)
    end
	return canvas,window
end
```

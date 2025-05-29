```
solve(prob::AbstractControlProblem, args...; kwargs...)
```

Solve the control problem defined by `prob`.

### Input

  * `prob` – controlled problem

Additional options are passed as arguments or keyword arguments; see the notes below for details. See the online documentation for examples.

### Output

The solution of a reachability problem controlled by a periodic controller. The control signals are stored in the `ext` field with each flowpipe.

### Notes

#### Mandatory arguments

  * Use the `tspan` keyword argument to specify the time span (start time and time

horizon); it can be a tuple, an interval, or a vector with two components. Alternatively, use the `T` keyword argument to specify only the time horizon, in which case the start time is assumed to be zero.

  * Use the `algorithm_plant` keyword argument to specify the algorithm for the

plant.

  * Use the `algorithm_controller` keyword argument to specify the algorithm for

the controller.

#### Optional arguments

  * Use the `splitter` and `input_splitter` keyword arguments to specify a

splitter.

Default: `NoSplitter()`

  * Use the `reconstruction_method` keyword arguments to specify a reconstruction

method for the interface between plant and controller.

Default: `TaylorModelReconstructor()`

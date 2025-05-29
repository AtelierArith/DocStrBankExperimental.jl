`Frame` represents the current execution state in a particular call frame. Fields:

  * `framecode`: the [`FrameCode`](@ref) for this frame.
  * `framedata`: the [`FrameData`](@ref) for this frame.
  * `pc`: the program counter (integer index of the next statment to be evaluated) for this frame.
  * `caller`: the parent caller of this frame, or `nothing`.
  * `callee`: the frame called by this one, or `nothing`.

The `Base` functions `show_backtrace` and `display_error` are overloaded such that `show_backtrace(io::IO, frame::Frame)` and `display_error(io::IO, er, frame::Frame)` shows a backtrace or error, respectively, in a similar way as to how Base shows them.

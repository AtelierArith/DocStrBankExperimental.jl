```
ret = debug_command(interp::Interpreter, frame::Frame, cmd::Symbol, rootistoplevel::Bool=false;
                    line::Union{Nothing,Integer}=nothing)
ret = debug_command(frame::Frame, cmd::Symbol, rootistoplevel::Bool=false; line=nothing)
```

Perform one "debugger" command. The keyword arguments are not used for all debug commands. `cmd` should be one of:

  * `:n`: advance to the next line
  * `:s`: step into the next call
  * `:sl` step into the last call on the current line (e.g. steps into `f` if the line is `f(g(h(x)))`).
  * `:sr` step until the current function will return
  * `:until`: advance the frame to line `line` if given, otherwise advance to the line after the current line
  * `:c`: continue execution until termination or reaching a breakpoint
  * `:finish`: finish the current frame and return to the parent

or one of the 'advanced' commands

  * `:nc`: step forward to the next call
  * `:se`: execute a single statement
  * `:si`: execute a single statement, stepping in if it's a call
  * `:sg`: step into the generator of a generated function

`rootistoplevel` and `ret` are as described for [`JuliaInterpreter.maybe_reset_frame!`](@ref).

```julia
CreateContext(
;
    exit_on_completion,
    show_test_window
) -> ImGuiTestEngine.Engine

```

Create a test engine context. The keyword arguments don't do anything in this library, they're used to support the test engine in CImGui.jl's renderloop.

# Arguments

  * `exit_on_completion=true`: Exit the program after the tests have completed.
  * `show_test_window=true`: Call [`ShowTestEngineWindows()`](@ref) while running the tests.

# Examples

```julia
engine = te.CreateContext()
```

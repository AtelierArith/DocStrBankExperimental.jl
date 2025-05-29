```julia
mutable struct ImGuiTest
```

Wrapper around the upstream `ImGuiTest`. Don't create this yourself, use [`@register_test()`](@ref). Once it's created you can assign functions to these properties:

  * `GuiFunc::Function`, for standalone GUI code that you want to run/test. This shouldn't be necessary if you're testing your own GUI.
  * `TestFunc::Function`, for tests that you want to execute.

The functions you assign must take in one argument to a [`TestContext`](@ref).

!!! danger
    This a memory-unsafe type, only use it while the engine is alive.


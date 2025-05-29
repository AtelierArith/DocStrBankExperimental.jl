```
StackFrameCategory(modcat=FlameGraphs.default_modcat,
                   loccat=FlameGraphs.default_loccat,
                   colorbg=colorant"white",
                   colorfont=colorant"black")
```

Colorize stackframes based on their category.

`modcat(mod::Module)` should return a color based on the stackframe's module, or `nothing` if it cannot categorize the stack frame based on the module.

`loccat(sf::StackFrame)` must return a color. It can use any of the fields of the stackframe, but `func`, `file`, `line`, and `from_c` might be common choices.

`colorbg` is the background color, and `colorfont` stores the choice of font color.

# Examples

```julia
using Plots, Profile, FlameGraphs
@profile plot(rand(5))    # "time to first plot"
g = flamegraph(C=true)
img = flamepixels(StackFrameCategory(), g)
```

Or you can tweak the coloration yourself:

```julia
function modcat(mod)
    mod == Plots && return colorant"purple"
    return nothing
end
img = flamepixels(StackFrameCategory(modcat), g)
```

```
tabpanelgroup(args...; kwargs...)
```

`tabpanelgroup` are a way of displaying more information using less window real estate.

---

### Examples

---

### Model

```julia-repl
julia> @vars TabPanelModel begin
            gpanel::R{String} = "panel"
       end
```

### View

```julia-repl
julia> Html.div(class="q-pa-md", [
          Html.div(class="q-gutter-y-md", style="max-width: 350px", [
             tabpanelgroup(:gpanel, animated=true, swipeable=true, infinite=true,
                   class="bg-purple text-white shadow-2 rounded-borders", [
                   tabpanel("Lorem ipsum dolor sit amet consectetur
                    adipisicing elit.", name="mails", [
                   Html.div("Mails", class="text-h6")
             ]),
            
             tabpanel("Lorem ipsum dolor sit amet consectetur
                  adipisicing elit.", name="alarms", [
                        Html.div("Alarms", class="text-h6")
             ]),

             tabpanel("Lorem ipsum dolor sit amet consectetur
                  adipisicing elit.", name="movies", [
                        Html.div("Movies", class="text-h6")
                  ]),
             ])
          ])
       ])
```

---

### Arguments

---

1. Behaviour

      * `keepalive::Bool` - Equivalent to using Vue's native <keep-alive> component on the content
      * `keepaliveinclude::Union{String,Vector}` - Equivalent to using Vue's native include prop for <keep-alive>; Values must be valid Vue component names (e.g. `"a,b"` `"/a|b/"` `['a', 'b']`)
      * `keepaliveexclude::Union{String,Vector}` - Equivalent to using Vue's native exclude prop for <keep-alive>; Values must be valid Vue component names (e.g. `"a,b"` `"/a|b/"` `['a', 'b']`)
      * `keepalivemax::Int` - Equivalent to using Vue's native max prop for <keep-alive> (e.g. `2`)
      * `animated::Bool` - Enable transitions between panel (also see 'transition-prev' and 'transition-next' props)
      * `infinite::Bool` - Makes component appear as infinite (when reaching last panel, next one will become the first one)
      * `swipeable::Bool` - Enable swipe events (may interfere with content's touch/mouse events)
      * `vertical::Bool` - Default transitions and swipe actions will be on the vertical axis
      * `transitionprev::String` - One of Quasar's embedded transitions (has effect only if 'animated' prop is set) (e.g. `"fade"` `"slide-down"`)
      * `transitionnext::String` - One of Quasar's embedded transitions (has effect only if 'animated' prop is set) (e.g. `"fade"` `"slide-down"`)

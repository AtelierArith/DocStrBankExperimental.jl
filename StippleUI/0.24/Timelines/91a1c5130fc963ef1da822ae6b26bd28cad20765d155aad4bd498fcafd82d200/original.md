```
  timeline(args...; kwargs...)
```

The `timeline` component displays a list of events in chronological order. It is typically a graphic design showing a long bar labelled with dates alongside itself and usually events. Timelines can use any time scale, depending on the subject and data.      

---

### Examples

---

### View

```julia-repl
julia> Html.div(class="q-px-lg q-pb-md", [
            timeline(color="secondary", [
            timelineentry("Timeline Heading", heading=true),
            timelineentry(title="Event Title", subtitle="February 22, 1986", [
            Html.div("Lorem ipsum dolor sit amet, consectetur adipisicing elit,
                  sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                  Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
                  nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in
                  reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
                  Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia
                  deserunt mollit anim id est laborum.")
            ]),
            timelineentry(title="Event Title", subtitle="February 21, 1986", icon="delete",[
            Html.div("Lorem ipsum dolor sit amet, consectetur adipisicing elit,
                  sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                  Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
                  nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in
                  reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
                  Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia
                  deserunt mollit anim id est laborum.")
            ]),
            timelineentry(title="Event Title",
            subtitle="February 22, 1986",
            avatar="https://cdn.quasar.dev/img/avatar2.jpg", [
            Html.div("Lorem ipsum dolor sit amet, consectetur adipisicing elit,
                  sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                  Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
                  nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in
                  reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
                  Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia
                  deserunt mollit anim id est laborum.")
            ])
            ])
       ])
```

---

### Arguments

---

1. Behavior

      * `side::String` - Side to place the timeline entries in dense and comfortable layout; For loose layout it gets overridden by `timelineentry` side prop. (default: `"right"`) | ex. `"left"` | `"right"`
      * `layout::String` - Layout of the timeline. Dense keeps content and labels on one side. Comfortable keeps content on one side and labels on the opposite side. Loose puts content on both sides. (default: `"dense"`) | ex. `"comfortable"` | `"loose"` | `"dense"`
2. Style

      * `color::String` - Color name for component from the Quasar Color Palette. ex. `"primary"` | `"teal-10"`
      * `dark::Bool` - Notify the component that the background is a dark color

```
  timelineentry(args...; kwargs...)
```

---

### Examples

---

### View

```julia-repl
julia> timelineentry(title="Event Title", subtitle="February 21, 1986", icon="delete",[
            Html.div("Lorem ipsum dolor sit amet, consectetur adipisicing elit,
                  sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                  Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
                  nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in
                  reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
                  Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia
                  deserunt mollit anim id est laborum.")
       ])
```

---

### Arguments

---

1. Behavior

      * `side::String` -  Side to place the timeline entry; Works only if `timeline` layout is loose. (default: `"right"`) | ex. `"left"` | `"right"`
2. Content

      * `tag::String` - Tag to use, if of type 'heading' only. (default: `"h3"`) | ex. `"h1"` | `"h2"` | `"h3"` | `"h4"` | `"h5"` | `"h6"`
      * `heading::Bool` - Defines a heading timeline item
      * `icon::String` - Icon name following Quasar convention; Make sure you have the icon library installed unless you are using 'img:' prefix; If 'none' (String) is used as value then no icon is rendered (but screen real estate will still be used for it). (ex. `"map"` | `"ion-add"`)
      * `avatar::String` - URL to the avatar image; Icon takes precedence if used, so it replaces avatar.
      * `title::String` - Title of timeline entry; Is overridden if using 'title' slot
      * `subtitle::String` - Subtitle of timeline entry; Is overridden if using 'subtitle' slot
      * `body::String` - Body content of timeline entry; Use this prop or the default slot
3. Style

      * `color::String` - Color name for component from the Quasar Color Palette

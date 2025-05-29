```
  card(args...; kwargs...)
```

`Card` component is a great way to display important pieces of grouped content. The `Card` component is intentionally lightweight and essentially a containing element that is capable of “hosting” any other component that is appropriate.

---

### Examples

---

### Model

```julia-repl
julia> @vars CardModel begin
          lorem::R{String} = "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
          url::R{String} = "https://cdn.quasar.dev/img/parallax2.jpg"
       end
```

### View

```julia-repl
julia> card(class="my-card", [
          imageview(src=:url, no__transition=true, [
            Html.div("Title", class="absolute-bottom text-h6")
          ]),
          card_section("{{lorem}}")
       ])
```

---

### Arguments

---

1. Content     * `tag::String` - HTML tag to render default `"div"` ex. `"div"` `"form"`
2. Style     * `dark::Bool` - Notify the component that the background is a dark color     * `square::Bool` - Removes border-radius so borders are squared     * `flat::Bool` - Applies a 'flat' design (no default shadow)     * `bordered::Bool` - Applies a default border to the component

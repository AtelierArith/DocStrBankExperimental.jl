---

### Examples

---

```
card_actions()
```

### Model

```julia-repl
julia> @vars CardModel begin
          lorem::R{String} = "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
       end
```

### View

```julia-repl
julia> card(class="my-card bg-secondary text-white", [
          card_section([
            Html.div("Our Changing Planet", class="text-h6"),
            Html.div("by John Doe", class="text-subtitle2")
          ]),
          card_section("{{ lorem }}"),
          card_actions([
            btn(flat=true, "Action 1"),
            btn(flat=true, "Action2")
          ])
        ])
```

---

### Arguments

---

  * `align::String` - Specify how to align the actions ("left", "center", "right", "between", "around", "evenly", "stretch")
  * `vertical:Bool` - Display actions one below the other

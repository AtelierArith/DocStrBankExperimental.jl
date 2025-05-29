```
  item(args...; kwargs...)
```

---

### Arguments

---

1. Content

      * `tag::String` - HTML tag to render; Suggestion: use 'label' when encapsulating a `checkbox`/`radio`/`toggle` so that when user clicks/taps on the whole item it will trigger a model change for the mentioned components ex. `a` `label` `div`
      * `insetlevel::Int` - Apply an inset; Useful when avatar/left side is missing but you want to align content with other items that do have a left side, or when you're building a menu ex. `insetlevel!="1"`
2. General

      * `tabindex::Union{Int, String}` - Tabindex HTML attribute value ex. `0` `100`
3. Navigation

      * `href::String` - Native <a> link href attribute; Has priority over the 'to'/'exact'/'replace' props ex. `http://genieframework.com`
      * `target::String` - Native <a> link target attribute; Use it only along with 'href' prop; Has priority over the 'to'/'exact'/'replace' props `_blank` `_self` `_parent` `_top`
4. State

      * `disable::Bool` - Put component in disabled mode
      * `active::Bool` - Put item into 'active' state
      * `clickable::Bool` - Is `item` clickable? If it's the case, then it will add hover effects and emit 'click' events
      * `manualfocus::Bool` - Put item into a manual focus state; Enables 'focused' prop which will determine if item is focused or not, rather than relying on native hover/focus states
      * `focused::Bool` - Determines focus state, ONLY if 'manual-focus' is enabled / set to true
5. Style

      * `dark::Bool` - Notify the component that the background is a dark color
      * `dense::Bool` - Dense mode; occupies less space

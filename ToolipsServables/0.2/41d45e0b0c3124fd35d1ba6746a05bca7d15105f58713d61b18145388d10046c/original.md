```julia
keyframes(name::String) -> ::KeyFrames
```

Constructs a `:keyframes` `Animation`, which can have frames added with `keyframes!`. To `keyframes!` we provide,  `to`, `from`, or a percentage with style pairs to create an animation.

```example
frames = keyframes("fadein")

keyframes!(frames, from, "opacity" => 0percent)
keyframes!(frames, to, "opacity" => 100percent)
# we may now use `style!`, making sure to `write!` our `Animation` as it is a `StyleComponent`.
mycomp = h2("heading", text = "this text fades in")

style!(mycomp, frames)
```

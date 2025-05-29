```
@register_inverse f g
@register_inverse f g left
@register_inverse f g right
```

Mark `f` and `g` as inverses of each other. By default, assume that `f` and `g` are bijective. Also defines `left_inverse` and `right_inverse` to call `inverse`. If the third argument is `left`, assume that `f` is injective and `g` is its left inverse. If the third argument is `right`, assume that `f` is surjective and `g` is its right inverse.

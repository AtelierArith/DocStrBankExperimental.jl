```
@register_inverse f g
@register_inverse f g left
@register_inverse f g right
```

`f` と `g` を互いの逆関数としてマークします。デフォルトでは、`f` と `g` が全単射であると仮定します。また、`left_inverse` と `right_inverse` を定義して `inverse` を呼び出します。第三引数が `left` の場合、`f` が単射であり、`g` がその左逆関数であると仮定します。第三引数が `right` の場合、`f` が全射であり、`g` がその右逆関数であると仮定します。

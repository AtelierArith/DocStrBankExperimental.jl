```
Editable(x::Bool[, true_string="true", false_string="false")
```

Create a Pluto widget that contain a Boolean value.

The displayed HTML will create a span with a green background that displays the custom string `true_string` when true and the `false_string` when false. If not provided, the second argument `true_string` defaults to "true" and the third one the "false".

The widget will trigger a bond update when clicking on it.

![991b712a-d62d-4036-b096-fe0fc52c9b25](https://github.com/disberd/PlutoExtras.jl/assets/12846528/f12e3bc3-f78c-45b5-b5fd-06f2083fc5c4)

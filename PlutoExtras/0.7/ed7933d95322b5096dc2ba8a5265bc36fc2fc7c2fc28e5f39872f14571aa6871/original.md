```
StringOnEnter(default::AbstractString)
```

Creates a Pluto widget that allows to provide a string as output when used with `@bind`.

Unlike the custom "TextField" from PlutoUI this only triggers a bond update upon pressing Enter or moving the focus out of the widget (similar to [`Editable`](@ref))

When rendered in HTML, the widget text will be shown with a dark yellow background.

![868c1c6e-8731-4465-959e-58cf551b9f61](https://github.com/disberd/PlutoExtras.jl/assets/12846528/782360f2-595a-4bbe-9769-5ddfaa144611)

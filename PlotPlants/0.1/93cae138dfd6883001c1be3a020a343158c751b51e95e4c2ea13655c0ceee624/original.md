```
latex_symbol(
            mid::String;
            sub::String = "",
            sup::String = "",
            presub::String = "",
            presup::String = "",
            option::String = "mathrm"
)
```

Return the latex symbol string, given

  * `mid` Center symbol, italic only when length>1
  * `sub` Optional: subscript after the `mid`
  * `sup` Optional: supscript after the `mid`
  * `presub` Optional: subscript before the `mid`
  * `presup` Optional: supscript before the `mid`
  * `option` Optional: choose from `text` and `mathrm` (default)

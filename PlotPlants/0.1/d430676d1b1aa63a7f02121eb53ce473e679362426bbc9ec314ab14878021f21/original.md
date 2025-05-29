```
latex_unit(id::String;
           paren::Bool = true,
           squared::Bool = false,
           space::Bool = true,
           unicode::Bool = false
)
```

Return the unit, given

  * `id` Identifier of the unit (if not in libary, use id as unit)
  * `paren` Optional: if true, include parenthesis
  * `squared` Optional: if true, use `[]`, otherwise, use `()`
  * `space` Optional: if true, add a SPACE at the beginning
  * `unicode` Optional. If true, return unicode; otherwise, return upgreek string

The predefined units include

  * `A` μmol CO₂ m⁻² s⁻¹
  * `E` mol H₂O m⁻² s⁻¹
  * `E_MMOL` mmol H₂O m⁻² s⁻¹
  * `G` mol m⁻² s⁻¹
  * `PAR` μmol m⁻² s⁻¹
  * `T` °C
  * `WUE` μmol mol⁻¹

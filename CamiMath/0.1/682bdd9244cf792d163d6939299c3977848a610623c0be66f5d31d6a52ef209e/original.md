```
dictUndoSmall
```

```
julia> dictUndoSmall
Dict{Char, Char} with 62 entries:
  'ᵉ' => 'e'
  'ₓ' => 'x'
  'ₖ' => 'k'
  'ⁿ' => 'n'
  '𐞥' => 'q'
  'ₕ' => 'h'
  ⋮   => ⋮
```

#### Example:

```
julia> get(dictUndoSmall, 'ⁿ', "not found")
'n': ASCII/Unicode U+006E (category Ll: Letter, lowercase)
```

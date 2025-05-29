```
dictSuperscript
```

```
julia> dictSuperscript
Dict{Char, Char} with 38 entries:
  'n' => 'ⁿ'
  'f' => 'ᶠ'
  'w' => 'ʷ'
  '1' => '¹'
  'd' => 'ᵈ'
  'e' => 'ᵉ'
  ⋮   => ⋮
```

#### 例:

```
julia> get(dictSuperscript, 'n', "not found")
'ⁿ': Unicode U+207F (category Lm: Letter, modifier)
```

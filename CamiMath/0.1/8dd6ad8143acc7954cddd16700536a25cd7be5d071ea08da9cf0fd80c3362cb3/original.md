```
dictSuperscript
```

```
julia> dictSubscript
Dict{Char, Char} with 25 entries:
  'n' => 'ₙ'
  '1' => '₁'
  'e' => 'ₑ'
  '7' => '₇'
  '6' => '₆'
  'o' => 'ₒ'
  ⋮   => ⋮
```

#### Example:

```
julia> get(dictSubscript, 'n', "not found")
'ₙ': Unicode U+2099 (category Lm: Letter, modifier)
```

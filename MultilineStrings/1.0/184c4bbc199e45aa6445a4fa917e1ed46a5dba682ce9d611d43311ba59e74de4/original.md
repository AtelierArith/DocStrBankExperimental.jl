```
multiline(str; style=:folded, chomp=:strip) -> AbstractString
```

Manipulate a multiline string according to the provided `style` and `chomp`. Works similarly to YAML multiline strings (also known as block scalars).

# Arguments

  * `str::AbstractString`: The multiline string to be processed

# Keywords

  * `style::Symbol`: Replace newlines with spaces (`:folded`) or keep newlines (`:literal`)
  * `chomp::Symbol`: No newlines at the end (`:strip`), single newline at the end (`:clip`), or keep all newlines from the end (`:keep`)

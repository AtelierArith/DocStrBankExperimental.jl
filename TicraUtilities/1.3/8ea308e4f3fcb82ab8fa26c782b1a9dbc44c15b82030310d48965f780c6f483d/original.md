```
write_cutfile(fname::AbstractString, cut::Cut, title::AbstractString="Cut file created by write_cutfile")

write_cutfile(fname::AbstractString, cuts::AbstractVector{Cut}, title::AbstractString="Cut file created by write_cutfile")
```

Write `Cut` cut data to a Ticra-compatible cut file.

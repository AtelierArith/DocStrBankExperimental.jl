```
multiline(str, indicators) -> AbstractString
```

Manipulate a multiline string according to the provided style and chomp encoded in the `indicators` string.

# Arguments

  * `str::AbstractString`: The multiline string to be processed
  * `indicators::AbstractString`: A terse string representing the style and chomp. Indicators can be either in letter-form or in YAML-form:

      * `fs` / `>-`: folded and strip
      * `fc` / `>`: folded and clip
      * `fk` / `>+`: folded and keep
      * `ls` / `|-`: literal and strip
      * `lc` / `|`: literal and clip
      * `lk` / `|"`: literal and keep

See [https://yaml-multiline.info](https://yaml-multiline.info) for more details.

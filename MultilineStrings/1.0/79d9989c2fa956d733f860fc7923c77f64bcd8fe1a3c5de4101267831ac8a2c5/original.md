```
@m_str -> String
```

Manipulate a multiline string literal according to a style and chomp indicator (provided after the ending quote):

  * Style indicator:

      * `f` replace newlines with spaces (folded, default)
      * `l` keep newlines (literal)
  * Chomp indicator:

      * `s` no newlines at the end (strip, default)
      * `c` single newline at the end (clip)
      * `k` keep all newlines from the end (keep)

If both a style and chomp indicator is provided the style indicator must be specified first.

Note string interpolation is still respected any newlines added from interpolation will be also be processed.

See [https://yaml-multiline.info](https://yaml-multiline.info) for more details.

# Examples

```jldoctest; setup = :(using MultilineStrings)
julia> m"""
       A string written
       over multiple lines
       """
"A string written over multiple lines"
```

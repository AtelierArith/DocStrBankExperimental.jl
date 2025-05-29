```
FontFamily(fonts ; font_mapping, font_modifiers, special_chars, slant_angle, thickness)
```

A set of font for LaTeX rendering.

# Required fields

  * `fonts` A with the path to 5 fonts (:regular, :italic, :bold, :bolditalic, and :math). The same font can be used for multiple entries, and unrelated fonts can be mixed.

# Optional fields

  * `font_mapping` a dict mapping the different character types (`:digit`, `:function`, `:punctuation`, `:symbol`, `:variable`) to a font identifier. Default to `MathTeXEngine._default_font_mapping`
  * `font_modifiers` a dict of dict, one entry per font command supported in the font set. Each entry is a dict that maps a font identifier to another. Default to `MathTeXEngine._default_font_modifiers`.
  * `specail_chars` mapping for special characters that should not be represented by their default unicode glyph (for example necessary to access the big integral glyph).
  * `slant_angle` the angle by which the italic fonts are slanted, in degree.
  * `thickness` the thickness of the lines associated to the font.

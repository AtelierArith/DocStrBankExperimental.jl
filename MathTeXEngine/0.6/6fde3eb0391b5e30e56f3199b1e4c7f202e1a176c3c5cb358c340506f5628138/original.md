```
TeXChar(char, font)
```

A MathTeX character with an associated font.

TeXChar implement all functions defined for FreeTypeAbstraction.FontExtents and can be used instead to get all geometric information about the character.

This is especially useful since for fonts that require some adjustement for the proper positioning of math symbols.

# Fields

```
- glyph_id::Culong The ID of the glyph representing the char in
    the associated font.
- font::FTFont The font that should be used to display this character.
- font_family::FontFamily The font family of the character.
- slanted::Bool Whether this char is considered italic.
- represented_char::Char The char represented by this char.
    Different from char for in some cases.
```

```
generate_tex_elements(str)
```

Create a list of tuple `(texelement, position, scale)` from a string of LaTeX math mode code. The elements' positions and scales are such as to approximatively reproduce the LaTeX output.

The elments are of one of the following types

```
- `TeXChar` a (unicode) character with a specific font.
- `HLine` a horizontal line.
- `VLine` a vertical line.
```

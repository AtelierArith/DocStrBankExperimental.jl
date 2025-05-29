```
preview()
```

If you're working in a notebook (eg Jupyter/IJulia), display a PNG or SVG file in the notebook.

If you're working in VS-Code, display a PNG or SVG file in the Plots pane.

Drawings of type :image should be converted to a matrix with `image_as_matrix()` before calling `finish()`.

Otherwise:

  * on macOS, open the file in the default application, which is probably the Preview.app for PNG and PDF, and Safari for SVG
  * on Unix, open the file with `xdg-open`
  * on Windows, refer to `COMSPEC`.

Returns the drawing.

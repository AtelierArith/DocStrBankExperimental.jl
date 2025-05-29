cameraproject - Projects 3D points into camera image

```
Usage:             xy = cameraproject(C, pt, computevisibility = false)
        (xy, visible) = cameraproject(C, pt, computevisibility = true)

Arguments:
             C - Camera structure.
            pt - 3xN matrix of 3D points to project into the image.

Keyword Argument:
 computevisibility - If set to true point visibility is returned
                     The default value is false.

Returns:
       xy      - 2xN matrix of projected image positions
       visible - Boolean array indicating whether the point is
                 within the field of view.  This is only evaluated if
                 'computevisibility is true and the camera structure has
                 non zero values for its 'rows' and 'cols' fields.

```

See also: Camera(), camstruct2projmatrix()

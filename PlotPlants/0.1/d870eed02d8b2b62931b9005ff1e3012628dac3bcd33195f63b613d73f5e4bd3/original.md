```
plot_ellipse!(
            ax::PyObject,
            xy::Tuple{Number,Number};
            width::Number = 10,
            height::Number = 10,
            angle::Number = 0,
            color::String = "black",
            edgecolor::String = color,
            facecolor::String = color,
            alpha::Number = 0.5
)
```

Plot an ellipse on axis, given

  * `ax` Axis to plot on
  * `xy` Center of the ellipse
  * `width` Width of the ellipse
  * `height` Height of the ellipse
  * `angle` Rotation angle of the ellipse
  * `color` Color of the ellipse
  * `edgecolor` Edgecolor of the ellipse
  * `facecolor` Face color of the ellipse
  * `alpha` Transparency of the ellipse

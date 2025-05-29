```
plot_stoma!(
           ax::PyObject,
           xy::Tuple{Number,Number};
           width::Number = 10,
           height::Number = 10,
           stoma::Number = 0.2,
           angle::Number = 0
)
```

Plot a stoma on the axis, given

  * `ax` Axis to plot on
  * `xy` Center of the stoma
  * `width` Width of the stoma
  * `height` Height of the stoma
  * `stoma` Stomatal pore width ratio
  * `angle` Rotation angle of the stoma

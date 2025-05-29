```
Scene TODO document this
```

## Constructors

## Fields

  * `parent`: The parent of the Scene; if it is a top-level Scene, `parent == nothing`.
  * `events`: [`Events`](@ref) associated with the Scene.
  * `px_area`: The current pixel area of the Scene.
  * `clear`: Whether the scene should be cleared.
  * `camera`: The `Camera` associated with the Scene.
  * `camera_controls`: The controls for the camera of the Scene.
  * `data_limits`: The limits of the data plotted in this scene. Can't be set by user and is only used to store calculated data bounds.

  * `transformation`: The [`Transformation`](@ref) of the Scene.
  * `plots`: The plots contained in the Scene.
  * `theme`
  * `attributes`
  * `children`: Children of the Scene inherit its transformation.
  * `current_screens`: The Screens which the Scene is displayed to.

  * `updated`: Signal to indicate whether layouting should happen. If updated to true, the Scene will be layouted according to its attributes (`raw`, `center`, or `scale_plot`).

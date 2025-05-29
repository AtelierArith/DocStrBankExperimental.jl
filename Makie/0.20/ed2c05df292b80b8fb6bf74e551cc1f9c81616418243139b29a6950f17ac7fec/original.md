```
Scene TODO document this
```

## Constructors

## Fields

  * `parent`: The parent of the Scene; if it is a top-level Scene, `parent == nothing`.
  * `events`: [`Events`](@ref) associated with the Scene.
  * `viewport`: The current pixel area of the Scene.
  * `clear`: Whether the scene should be cleared.
  * `camera`: The `Camera` associated with the Scene.
  * `camera_controls`: The controls for the camera of the Scene.
  * `transformation`: The [`Transformation`](@ref) of the Scene.
  * `plots`: The plots contained in the Scene.
  * `theme`
  * `children`: Children of the Scene inherit its transformation.
  * `current_screens`: The Screens which the Scene is displayed to.

  * `backgroundcolor`
  * `visible`
  * `ssao`
  * `lights`
  * `deregister_callbacks`
  * `cycler`

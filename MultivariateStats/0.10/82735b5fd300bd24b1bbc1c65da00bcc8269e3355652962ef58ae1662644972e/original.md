A multi-class linear discriminant model type has following fields:

  * `proj` is the projection matrix
  * `pmeans` is the projected means of all classes
  * `stats` is an instance of [`MulticlassLDAStats`](@ref) type that captures all statistics computed to train the model (which we will discuss later).

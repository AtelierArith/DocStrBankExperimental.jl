```
GSympNet(d)
```

Make a $G$-SympNet with dimension $d.$

There exists an additional constructor that can be called by supplying an instance of [`DataLoader`](@ref) (see [`LASympNet`](@ref) for an example of using this constructor).

# Arguments

Keyword arguments are:

  * `upscaling_dimension::Int = 2d`: The *upscaling dimension* of the gradient layer. See the documentation for [`GradientLayerQ`](@ref) and [`GradientLayerP`](@ref) for further explanation.
  * `n_layers::Int2`: The number of layers (i.e. the total number of [`GradientLayerQ`](@ref) and [`GradientLayerP`](@ref)).
  * `activationtanh`: The activation function that is applied.
  * `init_upper::Booltrue`: Initialize the gradient layer so that it first modifies the $q$-component.

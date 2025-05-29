```
Data_R = rotate_translate_scale(Data::Union{ParaviewData, CartData}; Rotate=0, Translate=(0,0,0), Scale=(1.0,1.0,1.0), Xc=(0.0,0.0))
```

Does an in-place rotation, translation and scaling of the Cartesian dataset `Data`.

# Parameters

Note that we apply the transformations in exactly this order:

  * `Scale`:        scaling applied to the `x,y,z` coordinates of the data set
  * `Rotate`:       rotation around the `x/y` axis (around the center of the box)
  * `Translate`:    translation
  * `Xc`:           center of rotation

# Example

```julia
julia> X,Y,Z   =   xyz_grid(10:20,30:40,-50:-10);
julia> Data_C  =   ParaviewData(X,Y,Z,(Depth=Z,))
ParaviewData
  size  : (11, 11, 41)
  x     ϵ [ 10.0 : 20.0]
  y     ϵ [ 30.0 : 40.0]
  z     ϵ [ -50.0 : -10.0]
  fields: (:Depth,)
julia> Data_R = rotate_translate_scale(Data_C, Rotate=30);
julia> Data_R
ParaviewData
  size  : (11, 11, 41)
  x     ϵ [ 8.169872981077807 : 21.83012701892219]
  y     ϵ [ 28.16987298107781 : 41.83012701892219]
  z     ϵ [ -50.0 : -10.0]
  fields: (:Depth,)
```

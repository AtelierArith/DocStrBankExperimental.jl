```
flatten_cross_section(V::CartData)
```

Takes a diagonal 3D cross*section and flattens it to be converted to a 2D Grid by create*CartGrid

# Example

```julia
Grid                    = create_CartGrid(size=(100,100,100), x=(0.0km, 99.9km), y=(-10.0km, 20.0km), z=(-40km,4km));
X,Y,Z                   = xyz_grid(Grid.coord1D...);
DataSet                 = CartData(X,Y,Z,(Depthdata=Z,));

Data_Cross              = cross_section(DataSet, dims=(100,100), Interpolate=true, Start=(ustrip(Grid.min[1]),ustrip(Grid.max[2])), End=(ustrip(Grid.max[1]), ustrip(Grid.min[2])))

x_new = flatten_cross_section(Data_Cross)

# This flattened cross_section can be added to original Data_Cross by addfield()

Data_Cross = addfield(Data_Cross,"FlatCrossSection", x_new)
CartData
    size    : (100, 100, 1)
    x       ϵ [ 0.0 : 99.9]
    y       ϵ [ -10.0 : 20.0]
    z       ϵ [ -40.0 : 4.0]
    fields  : (:Depthdata, :FlatCrossSection)
  attributes: ["note"]

```

```
CyclicArray
```

CyclicArray data structure. Available constructors:

```
CyclicArray(data::AbstractArray{T,N}, connections::AbstractArray)
```

To generate a new CyclicArray with the connections of x:

```
CyclicArray(x::CyclicArray)
```

To generate a new CyclicArray with the connections:

```
CyclicArray(connections)
```

To generate a new CyclicArray with the connections of y and data from x:

```
CyclicArray(x::AbstractArray,y::CyclicArray)
```

To generate a new CyclicArray with predifined connections:

```
CyclicArray(x::AbstractArray,str::String)
```

Available options:

"1D" - one dimensional array, one face

"1D2F" - one dimensional array, two faces

"2D" - two dimensional array, one face

"2DXY" - two dimensional array, one face, switching x-y directions

"2DFL" - two dimensional array, one face, flip sides

"3D" - three dimensional array, one face

"3DXY" - three dimensional array, one face, switching x-y directions

"cubed" - cubed sphere, three dimensional array, six faces

"cubed2D" - cubed sphere, two dimensional array, six faces

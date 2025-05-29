```
fits_create_img(f::FITSFile, A::AbstractArray)
```

Create a new primary array or IMAGE extension with the element type and size of `A`, that is capable of storing the entire array `A`.

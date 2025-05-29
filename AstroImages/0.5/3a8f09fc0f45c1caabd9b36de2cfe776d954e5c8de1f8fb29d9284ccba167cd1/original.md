```
shareheader(img::AstroImage, data) -> imgnew
```

Create a new image reusing the header dictionary of `img` but using the data of the AbstractArray `data`. The two images have synchronized header; modifying one also affects the other. See also: [`copyheader`](@ref).

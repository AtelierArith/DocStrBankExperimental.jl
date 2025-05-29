```
copyheader(img::AstroImage, data) -> imgnew
```

Create a new image copying the header of `img` but using the data of the AbstractArray `data`. Note that changing the header of `imgnew` does not affect the header of `img`. See also: [`shareheader`](@ref).

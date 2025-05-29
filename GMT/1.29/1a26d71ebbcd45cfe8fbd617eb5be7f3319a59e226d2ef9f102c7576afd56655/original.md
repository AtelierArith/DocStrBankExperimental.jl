```
I = togglemask(I::Union{GMTimage{<:Bool, 2}, GMTimage{<:UInt8, 2}}) -> GMTimage
```

Convert between UInt8 and Boolean representations of the mask images. A new object is returned with a copy of the input data.

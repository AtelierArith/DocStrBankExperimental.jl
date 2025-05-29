imerode - 2D morpholgical erosion with arbitrary structuring element

```
Usage:   eimg = imerode(img, se)

Arguments:
          img - Image to be eroded.  May be greyscale or binary
                ::Array{T,2} or ::BitArray{2}
           se - Structuring element defined by a 2D Bool array

Returns:
         eimg - eroded image
```

See also: imdilate(), circularstruct()

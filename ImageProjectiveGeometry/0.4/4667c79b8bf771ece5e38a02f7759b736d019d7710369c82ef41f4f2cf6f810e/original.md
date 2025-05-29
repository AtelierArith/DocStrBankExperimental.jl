imdilate - 2D morpholgical dilation with arbitrary structuring element

```
Usage:   dimg = imdilate(img, se)

Arguments:
          img - Image to be dilated.  May be greyscale or binary
                ::Array{T,2} or ::BitArray{2}
           se - Structuring element defined by a 2D Bool array

Returns:
         dimg - dilated image
```

See also: imerode(), circularstruct()

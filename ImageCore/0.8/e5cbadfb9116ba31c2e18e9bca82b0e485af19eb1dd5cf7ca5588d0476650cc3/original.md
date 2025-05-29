```
sdims(img)
```

Return the number of spatial dimensions in the image. Defaults to the same as `ndims`, but with ImagesAxes you can specify that some axes correspond to other quantities (e.g., time) and thus not included by `sdims`.

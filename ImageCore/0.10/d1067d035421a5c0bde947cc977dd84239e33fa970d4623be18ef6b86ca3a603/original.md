```
spacedirections(img) -> (axis1, axis2, ...)
```

Return a tuple-of-tuples, each `axis[i]` representing the displacement vector between adjacent pixels along spatial axis `i` of the image array, relative to some external coordinate system ("physical coordinates").

By default this is computed from `pixelspacing`, but you can set this manually using ImagesMeta.

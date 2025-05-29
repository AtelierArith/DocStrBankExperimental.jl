```
spacedirections(img)
```

Using ImageMetadata, you can set this property manually. For example, you could indicate that a photograph was taken with the camera tilted 30-degree relative to vertical using

```
img["spacedirections"] = ((0.866025,-0.5),(0.5,0.866025))
```

If not specified, it will be computed from `pixelspacing(img)`, placing the spacing along the "diagonal".  If desired, you can set this property in terms of physical units, and each axis can have distinct units.

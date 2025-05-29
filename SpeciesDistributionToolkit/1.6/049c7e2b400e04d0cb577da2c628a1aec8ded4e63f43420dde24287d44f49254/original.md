```
trim(layer::SDMLayer)
```

Returns a layer in which there are no empty rows/columns around the valued cells. This returns a *new* object. This will only remove the *terminal* empty rows/columns, so that gaps *inside* the layer are not affected.

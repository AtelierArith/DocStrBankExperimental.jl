```
export_scene(;scene, filename, kwargs...)
```

Export a screenshot of the current visualization (stored as `scene` as output of a call to `render`) as a PNG file store in the path given by `filename` (including `.png` extension). Keyword arguments will be passed along to the corresponding `save` method from Makie (see VPL documentation for details).

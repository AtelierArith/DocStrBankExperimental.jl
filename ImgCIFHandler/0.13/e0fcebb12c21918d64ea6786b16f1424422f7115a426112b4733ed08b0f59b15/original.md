```
get_gonio_axes(imgcif::CifContainer;check=false)
```

Return a list of goniometer axes, together with type (rotation/translation). Axes are in order of dependency chain, with base axis first. Typically omega-chi-phi.

```
save(filename::AbstractString,
     P::Union{Plot2D,Plot3D};
     runasy=true,
     forcepdf=false)
```

Save Asymptote figure. If `filename` has extension `.asy`, then an asy file is saved together with any auxiliary data files.

If `filename` has extension `.pdf`, `.svg` or `.png`, then only the resulting image file is saved to the location `filename`

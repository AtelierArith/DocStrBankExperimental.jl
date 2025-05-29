```
viz_fit(SampleData; DistFit=[], cumulative=false)
```

Visualizes sample data against fitted probability density functions (PDFs) and cumulative densidty functions (CDFs).

# Arguments

  * `SampleData`: Array of sample data.
  * `DistFit` (optional): Array of distribution types to fit.   If not provided, defaults to `[Normal, LogNormal, Uniform]`.

-`cumulative` (optional): Returns the results in cumulative form. Default is in probability density form.

# Returns

A plot object with the density of `SampleData` overlaid by the fitted PDFs / CDFs.

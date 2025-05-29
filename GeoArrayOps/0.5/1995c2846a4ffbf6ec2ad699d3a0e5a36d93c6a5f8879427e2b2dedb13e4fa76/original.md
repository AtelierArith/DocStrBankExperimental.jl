```
image = pssm(A; exaggeration=2.3, resolution=1.0)
```

Perceptually Shaded Slope Map by *Pingel, Clarke. 2014* [^pingel2014].

# Output

  * `image::Gray{T,2}` Grayscale image

# Arguments

  * `A::Array{Real,2}` Input Array
  * `exaggeration::Real=2.3` Factor to exaggerate elevation
  * `cellsize::Real=1.0` Size of cell to account for horizontal resolution if different from vertical resolution

[^pingel2014]: Pingel, Thomas, and Clarke, Keith. 2014. ‘Perceptually Shaded Slope Maps for the Visualization of Digital Surface Models’. Cartographica: The International Journal for Geographic Information and Geovisualization 49 (4): 225–40. [https://doi.org/10/ggnthv](https://doi.org/10/ggnthv).

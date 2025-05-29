```
create_imagej_macro_here(;MPP::Float64, minimum_segmentation_diameter::Float64)
```

Create a macro script for batch segmenting videos in `original_video` with Fiji.

Required keyword arguments:

  * `MPP` : microns per pixel, `Float64` (unique to your microscope setup!)
  * `minimum_segmentation_diameter` : only particles above this diameter*1.5 in microns will be segmented, `Float64`. See the following reference for why the 1.5:

J. Baumgartl, J. L. Arauz-Lara, and C. Bechinger, “Like-charge attraction in confinement: myth or truth?,”   Soft Matter, vol. 2, no. 8, p. 631, 2006, doi: 10.1039/b603052a.

# Example

```julia-repl
julia> create_imagej_macro_here(MPP=0.605, minimum_segmentation_diameter=4.5)
[ Info: ImageJ macro created at ~/tutorial/imagej_macro.ijm. See MicroTracker segmentation docs for instructions on how to use it. 
```

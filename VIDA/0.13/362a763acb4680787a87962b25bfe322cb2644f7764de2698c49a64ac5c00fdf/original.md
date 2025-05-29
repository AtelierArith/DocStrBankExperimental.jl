```julia
load_image(fname; polarization)

```

where `fname` is a image file. This will call a method based on the file extension. Curerntly we have .fits, and .h5 implemented.

# Details

This reads in a fits file that is more robust to the various imaging algorithms in the EHT, i.e. is works with clean, smili, eht-imaging.

The function returns an `IntensityMap` object that contains the relevant image and parameters extracted from the fits file. It also ensures that we are astronomers and that the image using sky-left coordinates.

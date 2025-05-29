```julia
load_hdf5(filename; polarization, style)

```

Loads an hdf5 movie file where `filename` should be a HDF5 file.

# Details

This reads in a hdf5 movie file and outputs and VIDAMovie object. If `polarization=true` we will read in all stokes parameters.

# Notes

Currently this only works with movies created by *ehtim*. 

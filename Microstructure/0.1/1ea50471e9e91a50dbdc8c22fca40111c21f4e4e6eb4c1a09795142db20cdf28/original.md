```
spherical_mean(
    image_file::String, 
    save::Bool=true, 
    acq_files::String...
)
```

Perform direction average on input DWI images `image_file` and return an MRI object with normalized spherical mean signal and associated imaging protocol. `image_file` is the full path of the DWI image file; `save` indicates whether to save the smt and normalized smt image volumes and protocol. If saving the files, nifti and text file (.btable) will be saved in the same path as the input data. Finall, variable number of `acq_files` are text files that tell you acquistion parameters of each DWI in the `image_file`.  Accepted file extensions are .bvals/.bvecs/.techo/.tdelta/.tsmalldel for b-values, gradient directions, echo times, diffusion gradient seperation and duration times.

Besides .bvals/.bvecs for conventional modelling, .tdelta/.tsmalldel files are needed for any models that estimate size, e.g. axon diameter, soma radius. .techo is needed if your data is collected with multiple echo-time and you want to do combined-diffusion relaxometry modelling.  The format of a .tdelta/.tsmalldel/.techo file is similar to a .bvals file (a vector with the length equal to the number of DWI volumes).  Unit in the .tdelta/.tsmalldel/.techo file is ms. 

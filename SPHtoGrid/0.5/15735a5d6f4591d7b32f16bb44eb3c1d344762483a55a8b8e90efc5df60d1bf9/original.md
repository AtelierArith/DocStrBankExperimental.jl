```
read_smac1_binary_info(filename::String)
```

Returns the image info in a `Smac1ImageInfo` struct.

## `Smac1ImageInfo` fields

  * `snap::Int32`:             number of input snapshot
  * `z::Float32`:              redshift of snapshot
  * `m_vir::Float32`:          virial mass of halo
  * `r_vir::Float32`:          virial radius of halo
  * `xcm::Float32`:            x coordinate of image center
  * `ycm::Float32`:            y coordinate of image center
  * `zcm::Float32`:            z coordinate of image center
  * `z_slice_kpc::Float32`:    depth of the image in kpc
  * `boxsize_kpc::Float32`:    xy-size of the image in kpc
  * `boxsize_pix::Float32`:    xy-size of the image in pixels
  * `pixsize_kpc::Float32`:    size of one pixel in kpc
  * `xlim::Array{Float64,1}`:  x limits of image
  * `ylim::Array{Float64,1}`:  y limits of image
  * `zlim::Array{Float64,1}`:  z limits of image
  * `units::String`:           unitstring of image

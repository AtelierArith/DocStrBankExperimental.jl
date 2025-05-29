```
struct Param
```

All the Parameters and their attributes that will be used in the simulation

  * `nx::Int64`: nx = nxe+1 , nxe is the number of energy grid that we will calculate for the energy in x direction
  * `ny::Int64`: ny = nye+1 , nye is the number of energy grid that we will calculate for the energy in y direction
  * `nxe::Int64`: number of energy grid that we will calculate for the energy in x direction
  * `nye::Int64`: number of energy grid that we will calculate for the energy in y direction
  * `num::Int64`: constant always set at 31 based on Measurement from Kirk, 1981 (The number of angle measurement in Kirk paper)
  * `nz::Int64`: number of the layer beneath the sea surface (in z direction) that we will calculate for the irradiance energy
  * `x::Vector{Float64}`: array of all the x corrdination
  * `y::Vector{Float64}`: array of all the y cooradination
  * `z::Vector{Float64}`: array of all the z coordination
  * `pex::Float64`: pex is being used in function pdfx or the function to calculate the partial derivative of the surface elevation in x direction
  * `pey::Float64`: pey is being used in function pdfx or the function to calculate the partial derivative of the surface elevation in y direction
  * `dx::Float64`: the distance between each grid point in x direction
  * `dy::Float64`: the distance between each grid point in y direction
  * `dz::Float64`: height difference between each layer that we calculate for the irradiance energy (nz)
  * `ztop::Float64`: the maximum height above the water surface
  * `xmin::Float64`: minimum x value (always set to 0)
  * `xmax::Float64`: maximum x value equal to multiplication between total number of grid point (nxe) and the distance between each grid point (dx) in x direction
  * `ymin::Float64`: minimum y value (always set to 0)
  * `ymax::Float64`: maximum y value equal to multiplication between total number of grid point (nye) and the distance between each grid point (dy) in y direction
  * `xl::Float64`: difference between the maximum and minimum value in x direction
  * `yl::Float64`: difference between the maximum and minimum value in y direction
  * `nxs::Int64`: nxs=nxη+1
  * `nys::Int64`: nys=nyη+1
  * `nxη::Int64`: same as nxeta value in the light.yml file: the number of wave grid point in x direction
  * `nyη::Int64`: same as nyeta value in the light.yml file: the number of wave grid point in y direction
  * `nxp::Int64`: number of grid in x direction that the photon will be emitted
  * `nyp::Int64`: number of grid in y direction that the photon will be emitted
  * `nphoton::Int64`: number of photon emitted
  * `kbc::Int64`: setting the mode of boundary condition: `kbc=1` (no interpolation) or periodic BC `kbc=0` (interpolation using FFT)
  * `a::Float64`: absortance coefficient
  * `b::Float64`: scattering coefficient
  * `kr::Float64`: the multiple of sphere detector radius to dz (not being used anywhere in the code)
  * `ddx::Float64`: the distance difference in x direction in which we will emit the photon (total length of physical grid xl devided by total number of photon grid nxp)
  * `ddy::Float64`: the distance difference in y direction in which we will emit the photon (total length of physical grid yl devided by total number of photon grid nyp)

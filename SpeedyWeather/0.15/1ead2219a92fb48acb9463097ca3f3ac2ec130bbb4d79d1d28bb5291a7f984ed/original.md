Earth's orography read from file, with smoothing.

  * `path::String`: path to the folder containing the orography file, pkg path default
  * `file::String`: filename of orography
  * `file_Grid::Type{<:SpeedyWeather.RingGrids.AbstractGrid}`: Grid the orography file comes on
  * `scale::Any`: scale orography by a factor
  * `smoothing::Bool`: smooth the orography field?
  * `smoothing_power::Any`: power of Laplacian for smoothing
  * `smoothing_strength::Any`: highest degree l is multiplied by
  * `smoothing_fraction::Any`: fraction of highest wavenumbers to smooth
  * `orography::Any`: height [m] on grid-point space.
  * `geopot_surf::Any`: surface geopotential, height*gravity [m²/s²]

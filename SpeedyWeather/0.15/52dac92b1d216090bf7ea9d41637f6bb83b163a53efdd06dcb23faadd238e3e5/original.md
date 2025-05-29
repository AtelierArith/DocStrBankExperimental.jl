Land-sea mask, fractional, read from file.

  * `path::String`: path to the folder containing the land-sea mask file, pkg path default
  * `file::String`: filename of land sea mask
  * `file_Grid::Type{<:SpeedyWeather.RingGrids.AbstractGrid}`: Grid the land-sea mask file comes on
  * `mask::Any`: Land-sea mask [1] on grid-point space. Land=1, sea=0, land-area fraction in between.

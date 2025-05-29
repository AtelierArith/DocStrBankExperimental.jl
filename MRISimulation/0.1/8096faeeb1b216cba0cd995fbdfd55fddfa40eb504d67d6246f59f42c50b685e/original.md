Getting (simulated) k-data using an explicit evaluation of the encoding operator

...

# Arguments

  * `tr::Abstract2DTrajectory` - Two-dimensional Trajectory
  * `image::Matrix`            - Image to be transformed
  * `correctionMap=[]`         - Correctionmap is summed up of the field offresonance and relaxation
  * `alpha::Float64 = 1.75`    - Oversampling factor
  * `m::Float64=4.0`           - Kenrel size
  * `K::Int64=28`              - Rank how much coefficients will be used to approx. correctionterm
  * `method="nfft"`            - Which Method used to get the approx. coefficients of correctionterm
  * (`sensmaps=[]`)            - array of coil sensitivities
  * `kargs...`                 - addional keyword arguments

...

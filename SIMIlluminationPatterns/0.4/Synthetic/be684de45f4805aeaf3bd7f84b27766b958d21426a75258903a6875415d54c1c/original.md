Serves to generate synthetic SIM data from a ground truth image.

The model of synthetic data generation is characterised by     a list of [`ModelComponent`](@ref)s which can be for instance:

  * **Noise** – black current noise, background noise, photon shot noise (additive   / multiplicative / etc. data dependent / independent)
  * **Downsampling** – downsampling the data so that the reconstruction could have the same size   as the ground truth ([`DownSampling`](@ref Synthetic.DownSampling))
  * **Illumination** – illumination of the focal plane / sample volume
  * **Optical transfer** – transfer of the light through the optical system

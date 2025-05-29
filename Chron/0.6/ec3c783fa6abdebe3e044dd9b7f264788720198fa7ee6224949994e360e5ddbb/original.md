```julia
BootstrapCrystDistributionKDE(data::AbstractArray, [sigma::AbstractArray]; cutoff=-0.05)
```

Bootstrap an estimate of the pre-eruptive (or pre-depositional) mineral crystallization distribution shape from a 1- or 2-d array of sample ages (one row per sample, one column per datum, padded with NaNs as needed) and an equivalent-size array of one-sigma uncertainties, using a kernel density estimate of stacked sample data.

### Examples

```julia
# Bootstrap crystallization distribution for a synthetic dataset with ages
# [1,2,3,...10] Ma and uncertainties of 1 Ma each
BootstrappedDistribution = BootstrapCrystDistributionKDE(1:10, ones(10))
```

```julia
BootstrapCrystDistributionKDE(smpl::ChronAgeData; cutoff=-0.05, [tpbloss=0])
```

Bootstrap an estimate of the pre-eruptive (or pre-depositional) mineral crystallization distribution shape from a Chron.ChronAgeData object containing data for several samples, using a kernel density estimate of stacked sample data.

If the samples provided as csv files in `smpl.Path` take the five-column form of U-Pb isotopic data files, the ages and uncertainties will be those of upper intercepts given a time of Pb-loss optionally specified as `tpbloss`.

Uncertainties will be treated as one or two-sigma absolute based on the value of `smpl.inputSigmaLevel`.

### Examples

```julia
BootstrappedDistribution = BootstrapCrystDistributionKDE(smpl)
```

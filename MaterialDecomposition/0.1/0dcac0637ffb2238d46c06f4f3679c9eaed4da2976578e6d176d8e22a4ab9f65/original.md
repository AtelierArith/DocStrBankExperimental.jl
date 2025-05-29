```
fit_calibration(calculated_calcium_intensities, calcium_densities, p0::AbstractVector=zeros(8))
```

Calibration equation, where `p0` is a vector of initial parameters that must be fit to underlying data  (`calculated_calcium_intensities`) which contains the "high" and "low" energy measurements for various  densities of calcium calibration rods (`known_calcium_densities`). `LsqFit.curve_fit` then returns calibrated  parameters `p`.

Note: `calculated_calcium_intensities` is expected to contain "low energy" intensity calculations in the first  column of the `n x 2` array and "high energy" intensity calculations in the second column of the `n x 2` array.

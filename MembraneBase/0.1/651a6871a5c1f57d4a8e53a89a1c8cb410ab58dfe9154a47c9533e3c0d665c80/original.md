```
jackknife_uncertainty(fitting_function, data)

Requirements:
    `data` can be any iterable, including custom structs.
    `fitting_function` must accept the the same iterable (data) which will be resampled, 
        it must return a vector of the fitted parameters.
This method will return a vector of uncertainties in the same order as the fitted parameters.
```

```
initialize(eki::EKP.EnsembleKalmanProcess, prior, output_dir)
initialize(ensemble_size, observations, noise, prior, output_dir)
```

Initialize a calibration, saving the initial parameter ensemble to a folder within `output_dir`.

If no EKP struct is given, construct an EKP struct and return it.

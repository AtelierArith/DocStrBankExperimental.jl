```
quantify(low_energy_intensity, high_energy_intensity, p, alg::MaterialDecomposition)
quantify(low_energy_intensity, high_energy_intensity, p, vol_ROI, alg::MaterialDecomposition)
```

Given a dual-energy CT image. First, calculate the measured intensity of a region of interest (ROI)  with suspected calcium for both low (`low_energy_intensity`) and high (`high_energy_intensity`) energy scans,  then utilize previously calibrated parameters (`p`) to calculate the  density of the suspected calcium within the ROI.

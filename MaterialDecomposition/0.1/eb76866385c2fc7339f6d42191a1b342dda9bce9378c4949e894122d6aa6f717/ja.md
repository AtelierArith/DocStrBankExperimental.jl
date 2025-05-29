```
quantify(low_energy_intensity, high_energy_intensity, p, alg::MaterialDecomposition)
quantify(low_energy_intensity, high_energy_intensity, p, vol_ROI, alg::MaterialDecomposition)
```

デュアルエネルギーCT画像が与えられた場合。まず、低エネルギー（`low_energy_intensity`）および高エネルギー（`high_energy_intensity`）スキャンの両方で、カルシウムが疑われる領域（ROI）の測定強度を計算し、その後、以前にキャリブレーションされたパラメータ（`p`）を利用して、ROI内の疑われるカルシウムの密度を計算します。

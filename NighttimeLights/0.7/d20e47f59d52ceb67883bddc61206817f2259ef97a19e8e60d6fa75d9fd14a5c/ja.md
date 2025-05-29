PSTT2021関数は、[But clouds got in my way: Bias and bias correction of VIIRS nighttime lights data in the presence of clouds, Ayush Patnaik, Ajay Shah, Anshul Tayal, Susan Thomas](https://www.xkdr.org/releases/PatnaikShahTayalThomas_2021_bias_PSTT2021_nighttime_lights.html)で説明されている新しいクリーニング手順のすべてのステップを従来のクリーニングとして実行します。

```julia
PSTT2021(radiance_datacube, ncfobs_datacube)
```

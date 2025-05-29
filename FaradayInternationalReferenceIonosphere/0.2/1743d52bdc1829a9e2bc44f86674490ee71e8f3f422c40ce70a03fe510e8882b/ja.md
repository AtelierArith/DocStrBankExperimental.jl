```
FaradayInternationalReferenceIonosphere
```

`FaradayInternationalReferenceIonosphere`は、Faraday-International Reference Ionosphere (FIRI)モデルプロファイルを扱うための便利な関数のコレクションです。

基盤となるFIRI-2018モデルの`DATA`、`HEADER`、および`ALTITUDE`には、例えば`FIRI.HEADER`としてアクセスできます。`ALTITUDE`の単位はメートルで、`DATA`は立方メートルあたりの電子数です。

関数`firi`のみがエクスポートされていますが、`FIRI.quantile`および`FIRI.extrapolate`も参照してください。

!!! tip
    短縮形のために、このパッケージを`julia using FaradayInternationalReferenceIonosphere import FaradayInternationalReferenceIonosphere as FIRI`のようにロードして、パッケージを`FIRI`として参照してください。


# References

Friedrich, M., Pock, C., & Torkar, K. (2018). FIRI-2018, an updated empirical model of the lower ionosphere. Journal of Geophysical Research: Space Physics, 123, 6737-6751. [doi: 10.1029/2018JA025437](https://doi.org/10.1029/2018JA025437)

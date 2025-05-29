Computes the spectral envelope of the given time-series.

```
input:

- ts: the time series to analyse
- m : the degree of smoothing wished.
      m corresponds to the number of neighbooring points that are mixed
      with given point to realize the smoothing.

output:

- Frequencies : list of points corresponding to the involved frequencies.
                contained in [0,0.5]
- amplitude : values of the spectral envelope for each given frequency point.
- eigenvectors : the optimal scaling for the different categories, for each frequency point.
- categories : the list of categories present in the data.
```

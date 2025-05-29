```
meanfreq(x, fs)
```

Calculate the mean power frequency of `x` with a sampling frequency of `fs`, defined as:

$$
MPF = \frac{\sum_{i=1}^{F} f_i X_i^2 }{\sum_{i=0}^{F} X_i^2 } Hz
$$

where $F$ is the Nyquist frequency, and $X$ is the power spectral density.

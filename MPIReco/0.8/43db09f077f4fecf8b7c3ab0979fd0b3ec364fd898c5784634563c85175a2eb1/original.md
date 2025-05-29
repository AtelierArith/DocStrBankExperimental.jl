```
findPeaks(data; stdTh=1.5, minBinDist=0, minBin=1)
```

Find peaks in the data.

  * data:         column vector of data
  * stdTh:        peaks are at least stdTh*standarddeviation above the mean
  * minBinDist:   min number of bins between two peaks
  * minBin:       no peaks in bins below minBin
  * return:       peak bins

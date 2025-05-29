```
Formants(fname; mdnFilt=true, avgFilt=true, outlierFilt=false)
```

Constructs a `Formants` object from tabular formant data contained in the file `fname` refers to. See Story & Bunton (2017, Vowel space density as an indicator of speech performance, *J. Acoust. Soc. Am. 141*(5), EL458-EL464) for more details on processing the formant data.

# Args

  * `fname` A `String` containing the name of the file of formant data to read in. The file is expected to be tab-delimited, where the first column has F1 measurements, and the second column has F2 measurements.
  * `mdnFilt` (keyword) Flag to perform a moving median filter on the formant data (current window size is set to 3)
  * `avgFilt` (keyword) Flag to perform a moving mean filter on the formant data (current window size is set to five)
  * `outlierFilt` (keyword) Flag to remove outlying formant observations (current threshold is set to remove rows where F1 >= 800 or F2 >= 2300); not specified in Story & Bunton (2017)

# Returns

A `Formants` object containing the array of formant values, as well as the values needed to undo the median transformation that is applied to the formant data.

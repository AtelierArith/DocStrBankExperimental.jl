```
neareyI(f1, f2, vowel, speaker)
```

Performs the Nearey formant extrinsic normalization routine, which logs the formants and subtracts the mean of all log formant values from each log formant value. See Nearey (1978, phonetic feature system for vowels, Indiania University Linguistics Club) for more details.

# Args

  * `f1`  F1 values
  * `f2` F2 values
  * `vowel` Vowel categories; not used in calculation, but passed in to keep them linked with their appropriate formant and speaker information
  * `speaker` An `Array` of speaker IDs; can be integers, symbols, string, and any other data type supported by the `groupby` function in the `DataFrames` package

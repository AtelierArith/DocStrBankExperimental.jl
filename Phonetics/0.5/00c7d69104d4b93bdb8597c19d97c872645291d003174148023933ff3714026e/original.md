```
lobanov(f1, f2, vowel, speaker)
```

Performs the Lobanov normalization routine, which calculates the z-score of each speaker's F1 and F2. See Lobanov (1971, Classification of Russian vowels spoken by different speakers. J. Acoust. Soc. Am. 49(2B), 606–608) for more details.

# Args

  * `f1`  F1 values
  * `f2` F2 values
  * `vowel` Vowel categories; not used in calculation, but passed in to keep them linked with their appropriate formant and speaker information
  * `speaker` An `Array` of speaker IDs; can be integers, symbols, string, and any other data type supported by the `groupby` function in the `DataFrames` package

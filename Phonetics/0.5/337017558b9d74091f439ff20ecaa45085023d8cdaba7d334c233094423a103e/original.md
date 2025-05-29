```
VowelSpace(formants::Formants; temporalNorm=true)
```

Constructor for a `VowelSpace` based on `formants`. Though this function is not an exact implementation, see Story & Bunton (2017, Vowel space density as an indicator of speech performance, *J. Acoust. Soc. Am. 141*(5), EL458-EL464) for more details on calculating the vowel space and the vowel space density.

# Args

  * `formants` A `Formants` object from which to create the `VowelSpace` (and corresponding density)
  * `temporalNorm` (keyword) Flag to divide the density counts by the number of discrete time steps in `formants`. Accounts for temporal differences that occur between recordings of different lengths, which will affect the density counts

# Returns

A `VowelSpace` object representing the calculated vowel space and density.

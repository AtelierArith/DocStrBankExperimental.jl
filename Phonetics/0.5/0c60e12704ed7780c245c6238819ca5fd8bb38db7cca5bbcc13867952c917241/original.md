```
generateFormants(nTokens; [cats=["iy", "aa", "uw"], gender=["w", "m"]])
```

Generate synthetic formants from multivariate normal distributions based on observations from  Hillenbrand et al. (1995, Acoustic characteristics of American English vowels, DOI: 10.1121/1.411872). Currently supports generating vowels for /i/ as `"iy"`, /ɑ/ as `"aa"`, and /u/ as `"uw"`, using values for men as `"m"` and women as `"w"`. One observation was dropped from the women /ɑ/ token because the F2 value could not be measured when Hillenbrand et al. collected the data. Values in the mean vectors and covariance matrices were rounded to two decimal places.

# Args

  * `nTokens` The number of tokens to generate for each category and gender pairing
  * `cats` (keyword argument) A vector of vowel categories to generate tokens for
  * `gender` (keyword argument) A vector of gender categories to generate tokens for
  * `seed` A seed value for a `MersenneTwister` random number generator; allows for reproducible results; using the default value of `nothing` will use the system-generated random seed.
  * `rng` An `AbstractRNG` object to use for random number generation; if the default value of `nothing` is used, a `MersenneTwister` object will be created

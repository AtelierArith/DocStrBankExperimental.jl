```
findchainlength(T, cparams::Vector; eps=10^-6, verbose=false)
```

Estimate length of chain required for a particular set of chain parameters by calculating how long an excitation on the first site takes to reach the end. The chain length is given as the length required for the excitation to have just reached the last site after time T. The initial number of sites in cparams has to be larger than the findchainlength result.

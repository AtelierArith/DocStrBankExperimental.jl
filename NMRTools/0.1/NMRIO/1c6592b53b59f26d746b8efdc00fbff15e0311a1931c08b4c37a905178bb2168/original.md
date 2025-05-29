```
sumexpts(outputexpt, inputexpts...; weights=[])
```

Sum a collection of Bruker NMR experiments, with optional weighting factors. Data will be truncated to fit the shortest data file.

# Arguments

  * `outputexpt`: Output experiment name (string or integer)
  * `inputexpts...`: Input experiment names (strings or integers)
  * `weights`: Optional vector of weights for each input experiment

# Details

  * Experiment names should be either strings with filenames or integers converted to strings
  * If weights are supplied, the length must match the number of input experiments
  * First input experiment is used as a template for the output experiment
  * For 1D experiments, 'fid' files are added; for nD experiments, 'ser' files are added
  * Processed data files in pdata/1 are removed, other pdata subdirectories are deleted
  * Updates the title file with information about the summed experiments
  * Updates the number of scans in the acqus file to be the sum of individual experiments
  * Prompts before overwriting any existing experiment

```
Bgen(path; sample_path=nothing, delay_parsing=false)
```

Read in the Bgen file information: header, list of samples. Variants and genotypes are read separately.

  * `path`: path to the ".bgen" file.
  * `sample_path`: path to  ".sample" file, if applicable.
  * `idx_path`: path to ".bgi" file, defaults to `path * ".bgi`.

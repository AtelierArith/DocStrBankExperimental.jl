```
export_qmsim_individual_blupf90(map,id,individual,snpfile; append=true)
```

Export individual genotypes to a text file, `snpfile` with an integer code `id`, using a format supported by BLUPF90. If the file does not exist, the function creates a new file. If there is the same file name as `snpfile`, the funtion appends the data to existing file by default. If you want to recreate the file, please remove the file before calling this function, or use `append=false`.

```
qualify!(df::DataFrame; 
        lod = nothing, 
        loq = nothing, 
        lloq = nothing, 
        uloq = nothing, 
        lodsub = "<LOD", 
        loqsub = "<LOQ", 
        lloqsub = "<LLOQ", 
        uloqsub = ">ULOQ")
```

Replace data out of acceptable range.

  * `lod`: limit of detection; values are promoted to match columns whose name starts with "Data".
  * `loq`: limit of quantification; values are promoted to match columns whose name starts with "Data".
  * `lloq`: lower limit of quantification; values are promoted to match columns whose name starts with "Data".
  * `uloq`: upper limit of quantification; values are promoted to match columns whose name starts with "Data".
  * `lodsub`: substitution for value smaller than LOD.
  * `loqsub`: substitution for value smaller than LOQ.
  * `lloqsub`: substitution for value smaller than LLOQ.
  * `uloqsub`: substitution for value larger than ULOQ.

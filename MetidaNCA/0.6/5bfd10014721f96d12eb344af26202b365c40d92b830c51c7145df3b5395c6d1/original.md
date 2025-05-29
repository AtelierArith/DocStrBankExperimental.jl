```
nca!(data::PDSubject{T,O}; calcm = :lint, intpm = nothing, verbose = 0, warn = true, io::IO = stdout, modify! = identity, kwargs...) where T where O
```

Non-compartmental (NCA) analysis of pharmacodynamic data.

Results:

  * Rmax - max responce;
  * Tmax - time for maximum responce;
  * AUCABL - AUC above baseline;
  * AUCBBL - AUC below baseline;
  * AUCATH - AUC above threshold;
  * AUCBTH - AUC below threshold;
  * AUCNETB - AUCABL - AUCBBL;
  * AUCNETT - AUCATH - AUCBTH;
  * TABL - time above baseline;
  * TBBL - time below baseline;
  * TATH - time above threshold;
  * TBTH - time below threshold;
  * AUCBTW - AUC between baseline and threshold;

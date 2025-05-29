```
HipparcosIADLikelihood(;hip_id)
```

Load the Hipparcos IAD likelihood. By default, this fetches and catches the extracted Java Tool edition of the van Leeuwan reduction. 

Additional arguments:

  * `catalog`: path to the data directory. By default, will fetch from online and cache.
  * `renormalize=true`: renormalize the uncertainties according to Nielsen et al. (2020)
  * `attempt_correction=true`: perform ad-hoc correction of any corrupted scans according to G. Brandt et al. (2021)
  * `is_van_leeuwen=true`: set to false if using e.g. the 1997 reduction.   This impacts how the residuals are reconstructed. The 1997 version applied a time varying    parallax to high RV stars, while the van Leeuwan reduction did not. The van Leeuwan reduction   residuals are relative to the 7 or 9 parameter model (when applicable) while the 1997 version   is always relative to the 5 parameter solution, even when higher order terms are reported.

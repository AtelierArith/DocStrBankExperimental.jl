```
nca!(data::UPKSubject{T, O, VOL, V}; adm = :ev, calcm = :lint, intpm = nothing, verbose = 0, warn = true, io::IO = stdout, modify! = identity) where T where O where VOL where V
```

Non-compartmental (NCA) analysis of pharmacokinetic for urine data.

Results:

  * AUCall
  * AUClast
  * Rlast
  * Maxrate
  * Tmax
  * AR
  * Vol
  * Prec
  * ARsq
  * Rsq
  * Kel
  * LZ
  * LZint
  * Rsqn
  * HL
  * AUCinf

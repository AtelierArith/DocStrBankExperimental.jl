```
nca!(data::UPKSubject{T, O, VOL, V}; adm = :ev, calcm = :lint, intpm = nothing, verbose = 0, warn = true, io::IO = stdout, modify! = identity) where T where O where VOL where V
```

尿データの薬物動態に関する非区画（NCA）分析。

結果：

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

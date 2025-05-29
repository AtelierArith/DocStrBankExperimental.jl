```
nca!(data::DataSet{Subj}; adm = :ev, calcm = :lint, intpm = nothing, verbose = 0, warn = true, wm::Bool = false, io::IO = stdout, modify! = identity) where Subj <: AbstractSubject
```

  * `wm` - write output to DataSet metadata (`:ncalog` index).

Non-compartmental (NCA) analysis of PK/PD data.

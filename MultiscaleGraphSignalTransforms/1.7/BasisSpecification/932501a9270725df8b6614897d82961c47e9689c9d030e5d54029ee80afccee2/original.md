```
BS = BasisSpec(dvec, dvec_loc, c2f, description)
```

is a data structure for a BasisSpec object contaning the following fields:

  * `levlist::Vector{Tuple{Int, Int}}`: the integer sequence that specifies a particular basis
  * `c2f::Bool`: if true (default), this indicates that the basis comes from the coarse-to-fine dictionary; if false, this indicates that the basis comes from the fine-to-coarse dictionary
  * `description::String`: a description of the specified basis

Copyright 2015 The Regents of the University of California

Implemented by Jeff Irion (Adviser: Dr. Naoki Saito) | Translated to julia and revised by Naoki Saito, Feb. 22, 2017 Modified by Yiqun Shao, May. 20, 2018

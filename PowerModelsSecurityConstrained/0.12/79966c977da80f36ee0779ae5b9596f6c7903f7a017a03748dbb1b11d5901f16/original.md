An OPF formulation conforming to the ARPA-e GOC Challenge 2 specification.

This formulation is design for optimizing the second-stage contingency problems It is identical to `run_c2_opf_soft` except for the using different data parameters which may change between the basecase and contingencies, most notably the ramping constraints and time passage constant `delta`.

An OPF formulation with generator unit commitment conforming to the ARPA-e GOC Challenge 2 specification.

The primary departure from the PowerModels standard formulations are: (1) the addition of price sensitive loads with a corresponding value maximizing objective; (2) ramping constraints from a previous operating points; (3) the addition of penalized slack values for branch flow limits, i.e. soft constraints.

This model differs from the `c2_opf_soft` model by strictly enforcing power balance at the network buses.

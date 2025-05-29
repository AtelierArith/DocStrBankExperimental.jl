```julia
struct CRISPRn <: Crispulator.Cas9Behavior
```

CRISPR KO behavior is more complex since sgRNA-directed DNA damage repair is stochastic. We assume that 2/3 of repair events at a given locus lead to a frameshift, and that the screen is carried out in diploid cells. The assumption that only bi-allelic frame-shift mutations lead to a phenotype in CRISPRn screens for most sgRNAs is supported by the empirical finding that in-frame deletions mostly do not show strong phenotypes, unless they occur in regions encoding conserved residues or domains[^2]

[^2]: Horlbeck MA, Gilbert LA, Villalta JE, Adamson B, Pak RA, Chen Y, Fields AP, Park CY, Corn JE, Kampmann M, Weissman JS: Compact and highly active next- generation libraries for CRISPR-mediated gene repression and activation. *Elife* 2016, 5.

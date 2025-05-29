```
seq_descriptions(path::AbstractString)
seq_descriptions(reader::FASTAReader)
seq_descriptions(stream::IO)
```

Read a fasta file at `path` and return the *description* fields. Just adds convenience on top of FASTX functions.

# Examples

```jldoctest
julia> seq_descr = seq_descriptions(EXAMPLE_DATA_PATH);

julia> seq_descr[1]
"lcl|NC_000964.3_cds_NP_387882.1_1 [gene=dnaA] [locus_tag=BSU_00010] [db_xref=EnsemblGenomes-Gn:BSU00010,EnsemblGenomes-Tr:CAB11777,GOA:P05648,InterPro:IPR001957,InterPro:IPR003593,InterPro:IPR010921,InterPro:IPR013159,InterPro:IPR013317,InterPro:IPR018312,InterPro:IPR020591,InterPro:IPR024633,InterPro:IPR027417,PDB:4TPS,SubtiList:BG10065,UniProtKB/Swiss-Prot:P05648] [protein=chromosomal replication initiator informational ATPase] [protein_id=NP_387882.1] [location=410..1750] [gbkey=CDS]"
```

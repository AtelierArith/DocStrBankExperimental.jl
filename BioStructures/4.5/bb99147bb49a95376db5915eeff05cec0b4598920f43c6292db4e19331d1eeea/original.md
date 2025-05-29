```
downloadallobsoletepdb(; <keyword arguments>)
```

Download all obsolete Protein Data Bank (PDB) files from the RCSB server.

Returns the list of PDB IDs downloaded. Requires an internet connection.

# Arguments

  * `obsolete_dir::AbstractString=pwd()`: the directory where the PDB files are   downloaded; defaults to the current working directory.
  * `format::Type=PDBFormat`: the format of the PDB file; options are PDBFormat,   PDBXMLFormat and MMCIFFormat. MMTF files are no longer available to download.
  * `overwrite::Bool=false`: if set `true`, overwrites the PDB file if it exists   in `dir`; by default skips downloading the PDB file if it exists.

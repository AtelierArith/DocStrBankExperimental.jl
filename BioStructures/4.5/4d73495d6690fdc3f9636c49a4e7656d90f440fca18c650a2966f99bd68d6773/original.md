```
downloadentirepdb(; <keyword arguments>)
```

Download the entire Protein Data Bank (PDB) from the RCSB server.

Returns the list of PDB IDs downloaded. Ensure you have enough disk space and time before running. The function can be stopped any time and called again to resume downloading. Requires an internet connection.

# Arguments

  * `dir::AbstractString=pwd()`: the directory to which the PDB files are   downloaded; defaults to the current working directory.
  * `format::Type=PDBFormat`: the format of the PDB file; options are PDBFormat,   PDBXMLFormat and MMCIFFormat. MMTF files are no longer available to download.
  * `overwrite::Bool=false`: if set `true`, overwrites the PDB file if it exists   in `dir`; by default skips downloading the PDB file if it exists.

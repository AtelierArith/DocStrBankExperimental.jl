```
retrievepdb(pdbid::AbstractString; <keyword arguments>)
```

Download and read a Protein Data Bank (PDB) file or biological assembly from the RCSB server, returning a `MolecularStructure`.

Requires an internet connection.

# Arguments

  * `pdbid::AbstractString`: the PDB ID to be downloaded and read.
  * `dir::AbstractString=pwd()`: the directory to which the PDB file is   downloaded; defaults to the current working directory.
  * `format::Type=MMCIFFormat`: the format of the PDB file; options are PDBFormat,   PDBXMLFormat and MMCIFFormat. MMTF files are no longer available to download.
  * `obsolete::Bool=false`: if set `true`, the PDB file is downloaded in the   auto-generated "obsolete" directory inside the specified `dir`.
  * `overwrite::Bool=false`: if set `true`, overwrites the PDB file if it exists   in `dir`; by default skips downloading the PDB file if it exists.
  * `ba_number::Integer=0`: if set > 0 downloads the respective biological   assembly; by default downloads the PDB file.
  * `structure_name::AbstractString="$pdbid.pdb"`: the name given to the returned   `MolecularStructure`; defaults to the PDB ID.
  * `remove_disorder::Bool=false`: whether to remove atoms with alt loc ID not ' '   or 'A'.
  * `read_std_atoms::Bool=true`: whether to read standard ATOM records.
  * `read_het_atoms::Bool=true`: whether to read HETATOM records.
  * `run_dssp::Bool=false`: whether to run DSSP to assign secondary structure.   Requires the DSSP_jll.jl package to be imported if set to `true`.
  * `run_stride::Bool=false`: whether to run STRIDE to assign secondary structure.   Requires the STRIDE_jll.jl package to be imported if set to `true`.

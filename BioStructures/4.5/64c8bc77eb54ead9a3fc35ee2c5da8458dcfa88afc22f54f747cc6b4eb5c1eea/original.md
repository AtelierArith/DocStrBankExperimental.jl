```
read(filepath::AbstractString, format::Type; <keyword arguments>)
read(input::IO, format::Type; <keyword arguments>)
```

Read a Protein Data Bank (PDB) file and return a `MolecularStructure`.

# Arguments

  * `format::Type`: the format of the PDB file; options are PDBFormat, MMCIFFormat   and MMTFFormat. MMTFFormat requires the MMTF.jl package to be imported.
  * `structure_name::AbstractString`: the name given to the returned   `MolecularStructure`; defaults to the file name.
  * `remove_disorder::Bool=false`: whether to remove atoms with alt loc ID not ' '   or 'A'.
  * `read_std_atoms::Bool=true`: whether to read standard ATOM records.
  * `read_het_atoms::Bool=true`: whether to read HETATOM records.
  * `run_dssp::Bool=false`: whether to run DSSP to assign secondary structure.   Requires the DSSP_jll.jl package to be imported if set to `true`.
  * `run_stride::Bool=false`: whether to run STRIDE to assign secondary structure.   Requires the STRIDE_jll.jl package to be imported if set to `true`.
  * `gzip::Bool=false`: whether the input is gzipped, not available for PDB   format.

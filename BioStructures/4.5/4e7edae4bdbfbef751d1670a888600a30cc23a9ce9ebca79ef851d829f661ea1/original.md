```
downloadpdb(pdbid::AbstractString; <keyword arguments>)
downloadpdb(pdbid::AbstractArray{<:AbstractString, 1}; <keyword arguments>)
downloadpdb(f::Function, args...)
```

Download files from the Protein Data Bank (PDB) via RCSB.

When given an `AbstractString`, e.g. `"1AKE"`, downloads the PDB file and returns the path to the file. When given an `Array{<:AbstractString, 1}`, downloads the PDB files in the array and returns an array of the paths to the files. When given a function as the first argument, runs the function with the downloaded filepath(s) as an argument then removes the file(s). Requires an internet connection.

# Arguments

  * `dir::AbstractString=pwd()`: the directory to which the PDB file is   downloaded; defaults to the current working directory.
  * `format::Type=PDBFormat`: the format of the PDB file; options are PDBFormat,   PDBXMLFormat and MMCIFFormat. MMTF files are no longer available to download.
  * `obsolete::Bool=false`: if set `true`, the PDB file is downloaded in the   auto-generated "obsolete" directory inside the specified `dir`.
  * `overwrite::Bool=false`: if set `true`, overwrites the PDB file if it exists   in `dir`; by default skips downloading the PDB file if it exists.
  * `ba_number::Integer=0`: if set > 0 downloads the respective biological   assembly; by default downloads the PDB file.

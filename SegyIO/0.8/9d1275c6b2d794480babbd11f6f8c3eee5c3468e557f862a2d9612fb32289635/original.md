Use: fileheader = read_fileheader(s::IO, keys::Array{String,1}; bigendian::Bool = true)

Return a fileheader from stream 's' with the fields defined in 'keys'.

# Examples

Read the entire file header.

```
julia> s = open("data/testdata.segy")
IO(<file data/testdata.segy>)

julia> fh = SegyIO.read_fileheader(s)
SegyIO.BinaryFileHeader(9999, 9999, 1, 400, 0, 4000, 4000, 560, 560, 1, -13922, 4, 1, 0,
0, 0, 0, 0, 0, 0, 0, 2, 1, 4, 2, 0, 0, 0, 0, 0, Dict("expf"=>3226,"sfe"=>3234,
"rgc"=>3250,"jobid"=>3200,"dt"=>3216,"nsfr"=>3222,"slen"=>3236,"vpol"=>3258,"renum"=>3208,
"dsf"=>3224…))
```

Read only the sample interval and number of traces from the file header.

```
julia> s = open("data/testdata.segy")
IO(<file data/testdata.segy>)

julia> fh = SegyIO.read_fileheader(s, ["dt"; "ns"])
SegyIO.BinaryFileHeader(0, 0, 0, 0, 0, 4000, 0, 560, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
0, 0, 0, 0, 0, 0, 0, 0, 0, 0, Dict("expf"=>3226,"sfe"=>3234,"rgc"=>3250,"jobid"=>3200,
"dt"=>3216,"nsfr"=>3222,"slen"=>3236,"vpol"=>3258,"renum"=>3208,"dsf"=>3224…))
```

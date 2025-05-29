使用法: fileheader = read_fileheader(s::IO, keys::Array{String,1}; bigendian::Bool = true)

ストリーム's'から'keys'で定義されたフィールドを持つファイルヘッダーを返します。

# 例

ファイルヘッダー全体を読み取ります。

```
julia> s = open("data/testdata.segy")
IO(<file data/testdata.segy>)

julia> fh = SegyIO.read_fileheader(s)
SegyIO.BinaryFileHeader(9999, 9999, 1, 400, 0, 4000, 4000, 560, 560, 1, -13922, 4, 1, 0,
0, 0, 0, 0, 0, 0, 0, 2, 1, 4, 2, 0, 0, 0, 0, 0, Dict("expf"=>3226,"sfe"=>3234,
"rgc"=>3250,"jobid"=>3200,"dt"=>3216,"nsfr"=>3222,"slen"=>3236,"vpol"=>3258,"renum"=>3208,
"dsf"=>3224…))
```

ファイルヘッダーからサンプル間隔とトレース数のみを読み取ります。

```
julia> s = open("data/testdata.segy")
IO(<file data/testdata.segy>)

julia> fh = SegyIO.read_fileheader(s, ["dt"; "ns"])
SegyIO.BinaryFileHeader(0, 0, 0, 0, 0, 4000, 0, 560, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
0, 0, 0, 0, 0, 0, 0, 0, 0, 0, Dict("expf"=>3226,"sfe"=>3234,"rgc"=>3250,"jobid"=>3200,
"dt"=>3216,"nsfr"=>3222,"slen"=>3236,"vpol"=>3258,"renum"=>3208,"dsf"=>3224…))
```

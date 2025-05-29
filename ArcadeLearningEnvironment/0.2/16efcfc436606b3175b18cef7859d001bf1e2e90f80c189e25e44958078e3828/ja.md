```
getROMList()
```

利用可能なROMの名前の配列を返します。これらのROMは、フルパスを渡すのではなく、単にその名前を[`loadROM`](@ref)関数に渡すことでロードできます。

# 例

```julia-repl
julia> getROMList()
74-element Array{String,1}:
 "adventure"
 "air_raid"
 "alien"
 "amidar"
 "assault"
 "asterix"
 ⋮
 "venture"
 "video_pinball"
 "wizard_of_wor"
 "yars_revenge"
 "zaxxon"
```

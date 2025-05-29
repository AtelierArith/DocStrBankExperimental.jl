```
mapmmcif(mmcifdict, field1 => field2, field3 => field4, ...)
```

```jldoctest
julia> import BioStructures

julia> filename = BioStructures.downloadpdb("3HFM", format=BioStructures.MMCIFFormat);
[ Info: PDBからファイルをダウンロード中: 3HFM

julia> mmcifdict = BioStructures.MMCIFDict(filename);

julia> mapmmcif(mmcifdict,
           "_atom_site.auth_asym_id"   => "_atom_site.label_entity_id",
           "_entity_src_gen.entity_id" => "_entity_src_gen.pdbx_gene_src_ncbi_taxonomy_id")
Dict{String, String} with 3 entries:
  "Y" => "9031"
  "L" => "10090"
  "H" => "10090"
```

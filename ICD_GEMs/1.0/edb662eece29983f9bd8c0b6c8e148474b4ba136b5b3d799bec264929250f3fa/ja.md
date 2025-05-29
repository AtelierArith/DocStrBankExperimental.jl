```
get_GEM_dictionary_from_cdc_gem_txt(path_to_txt::String, direction::String)
```

`OrderedDict`を返し、[CDCウェブサイト](https://ftp.cdc.gov/pub/Health_Statistics/NCHS/Publications/ICD10CM/2018/Dxgem_2018.zip)からダウンロードされたGEMファイルを表します。`path_to_txt`は.txtファイルへのパスであり、`direction`はGEMファイルの方向（`"I9_I10"`または`"I10_I9"`、[`GEM`](@ref)を参照）です。

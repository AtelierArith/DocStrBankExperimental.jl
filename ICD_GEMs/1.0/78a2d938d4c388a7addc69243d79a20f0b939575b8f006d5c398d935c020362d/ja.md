```
get_gem_dataframe_from_cdc_gem_txt(path_to_txt::String, direction::String)
```

CDCのウェブサイトからダウンロードした.txtファイルから`GEM{DataFrame}`オブジェクトを取得します。[CDCウェブサイト](https://ftp.cdc.gov/pub/Health_Statistics/NCHS/Publications/ICD10CM/2018/Dxgem_2018.zip)からの.txtファイルへのパスは`path_to_txt`で、`direction`はGEMファイルの方向（`"I9_I10"`または`"I10_I9"`、[`GEM`](@ref)を参照）です。

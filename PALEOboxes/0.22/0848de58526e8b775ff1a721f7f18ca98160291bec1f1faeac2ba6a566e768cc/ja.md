```
create_model_from_config(
    config_file::AbstractString, configmodel::AbstractString;
    modelpars::Dict = Dict()
) -> model::Model

create_model_from_config(
    config_files,
    configmodel::AbstractString;
    modelpars::Dict = Dict()
) -> model::Model
```

単一の[YAML](https://en.wikipedia.org/wiki/YAML) `config_file`からモデルを構築するか、順番に読み込まれ、yamlとして解析される前に連結される`config_files`のコレクションから構築します。

オプションの引数`modelpars`は、`<configmodel>:`の`parameters:`セクションにあるパラメータを上書きするパラメータを提供します。

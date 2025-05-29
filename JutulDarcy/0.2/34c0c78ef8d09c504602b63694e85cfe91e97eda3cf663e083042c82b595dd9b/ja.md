```
case = setup_case_from_data_file(
    filename;
    parse_arg = NamedTuple(),
    kwarg...
)

case, data = setup_case_from_data_file(filename; include_data = true)
```

標準入力ファイル（拡張子 .DATA）から [`JutulCase`](@ref) を設定します。パーサーへの追加引数は、`parse_arg` として与えられる `NamedTuple` のキー/値として渡すことができます。オプションの入力 `include_data=true` を指定すると、関数はケース自体に加えて解析されたデータも返します。追加のキーワード引数は [`setup_case_from_parsed_data`](@ref) に渡されます。

```
find_files_in_allowed_folders(
    input_dirs::String...;
    eqdsk_file::String,
    recursive::Bool=true,
)
```

許可されたフォルダのリストを検索し、SOLPSケースに関する情報を提供するファイル名のセットを探します。完全なパスを持つファイル名のリストを返します。

例:

```julia
SOLPS2ctrl.find_files_in_allowed_folders(
    "<your samples folder>/D3D_Ma_184833_03600";
    eqdsk_file="g184833.03600",
)
```

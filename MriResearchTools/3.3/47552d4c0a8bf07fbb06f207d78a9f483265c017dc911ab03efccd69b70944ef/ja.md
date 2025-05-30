```
Ice_output_config(name, path, nslices, nfiles; nechoes=1, nchannels=1, dtype=Int16)

`name` はフルファイル名のユニークな部分であることができます
`nfiles` はフォルダ内の .ima ファイルの数です

例:
cfg = Ice_output_config("Aspire_P", "/path/to/ima_folder", 120, 720)
volume = read_volume(cfg)
```

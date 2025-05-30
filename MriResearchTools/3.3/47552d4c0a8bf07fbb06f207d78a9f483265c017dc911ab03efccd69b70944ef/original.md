```
Ice_output_config(name, path, nslices, nfiles; nechoes=1, nchannels=1, dtype=Int16)

`name` can be a unique part of the full file name
`nfiles` is the number of .ima files in the folder

Example:
cfg = Ice_output_config("Aspire_P", "/path/to/ima_folder", 120, 720)
volume = read_volume(cfg)
```

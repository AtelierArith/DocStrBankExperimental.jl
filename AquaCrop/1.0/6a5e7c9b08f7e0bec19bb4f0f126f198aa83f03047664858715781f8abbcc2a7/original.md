```
save_crop(file, cropfield::AquaCropField, head=nothing; kwargs...)
```

head          header to describe the file. Defaults to `head = "# Crop saved in "*string(today())`

Writes the crop into a toml file. Useful after tunning a crop

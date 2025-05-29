Button to download a Julia object as a file from the browser.

See [`FilePicker`](@ref) to do the opposite.

# Examples

```julia
DownloadButton("Roses are red,", "novel.txt")
```

```julia
DownloadButton(UInt8[0xff, 0xd8, 0xff, 0xe1, 0x00, 0x69], "raw.dat")
```

```julia
import JSON
DownloadButton(JSON.json(Dict("name" => "merlijn", "can_cook" => true)), "staff.json")
```

If you want to make a **local file** available for download, you need to `read` the file's data:

```julia
let
    filename = "/Users/fonsi/Documents/mydata.csv"
    DownloadButton(read(filename), basename(filename))
end
```

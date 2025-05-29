```
get_example_file(filename; head="main", output_directory=".", force=false)
```

Retrieve an example file from the [`ReadVTK_examples` repository](https://github.com/JuliaVTK/ReadVTK_examples) at commit/branch `head` and store it in the `output_directory`. If the file already exists locally, do not download the file again unless `force` is true. Return the local path to the downloaded file.

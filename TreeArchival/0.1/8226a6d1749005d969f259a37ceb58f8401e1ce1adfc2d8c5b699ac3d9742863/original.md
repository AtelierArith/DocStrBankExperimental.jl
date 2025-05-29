```
unarchive(source_path::String, output_dir::String;
          compressor = detect_compressor(source_path),
          stderr_out = stderr)
```

Read from `source_path`, automatically determine the compression type by inspecting the first few bytes, then write the unarchived result to `output_dir`.

If the compression type cannot be auto-determined, throws an error.

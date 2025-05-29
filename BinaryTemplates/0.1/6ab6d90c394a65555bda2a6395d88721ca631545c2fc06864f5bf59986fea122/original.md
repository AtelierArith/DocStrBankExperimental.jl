```
apply_template(target_filename, template::AbstractBinaryTemplate; backup_filename, ensure_zero=true, truncate=false)
```

Apply an `AbstractBinaryTemplate` to target_filename by writing chunks to the appropriate offsets.

The file will be enlarged to `expected_file_size(template)`.

# Keywords

  * `backup_filename` - Name of the file to store the backup template. Default: `BinaryTemplates.backup_filename(target_filename)`.
  * `ensure_zero` - Throws an error if the bytes to be overwritten are not `0x00`. Default: `true`
  * `truncate` - Truncate the file if it is larger than expected. Default: `false`

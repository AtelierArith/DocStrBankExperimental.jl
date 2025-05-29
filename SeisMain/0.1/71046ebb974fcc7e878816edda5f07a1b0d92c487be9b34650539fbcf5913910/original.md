```
download_if_needed(url::String, output::String, sha256sum::String)
```

Download the file from `url` to `output` if the file is not already present or if its SHA256 checksum does not match the `sha256sum`.

# Arguments

  * `url::String`: The URL from which to download the file.
  * `output::String`: The path where the downloaded file will be saved.

# Keyword arguments

  * `sha256sum::String`: The expected SHA256 checksum of the file to ensure its integrity.

# Output

  * `nothing`: This function returns `nothing`. It performs the side effect of downloading a file and verifying its checksum. If the checksum does not match, the function raises an error and deletes the downloaded file.

*Credits: Átila Saraiva Quintela Soares, 2024*

```
file(filepath::String; loadfile=nothing, status = 200, headers = []) :: HTTP.Response
```

Reads a file and returns a HTTP.Response. The file is read as binary. If the file does not exist,  an ArgumentError is thrown. The MIME type and the size of the file are added to the headers.

# Arguments

  * `filepath`: The path to the file to be read.
  * `loadfile`: An optional function to load the file. If not provided, the file is read using the `open` function.
  * `status`: The HTTP status code to be used in the response. Defaults to 200.
  * `headers`: Any additional headers to be included in the response. Defaults to an empty array.

# Returns

  * A HTTP response.

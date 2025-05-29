```
dcc_download(;kwargs...)
```

A Download component The Download component opens a download dialog when the data property changes.

  * `id` (String; optional): The ID of this component, used to identify dash components in callbacks.
  * `base64` (Bool; optional): Default value for base64, used when not set as part of the data property.
  * `data` (lists containing elements filename, content, base64, type   - `filename` (String; required): Suggested filename in the download dialogue.   - `content` (String; required): File content.   - `base64` (Bool; optional): Set to true, when data is base64 encoded.   - `type` (String; optional): Blob type, usually a MIME-type.; optional): On change, a download is invoked.
  * `type` (String; optional): Default value for type, used when not set as part of the data property.

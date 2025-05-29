```
uploadtolink(client::PCloudClient; kwargs...)
```

Upload file(s) to a upload link. Expects `code`.

Most things that apply to uploadfile also apply here, especially `progresshash` can be used in the same manner to monitor upload progress with uploadlinkprogress.

There is a slight difference that `renameifexists` is omitted and the uploaded file is always renamed when a file with the requested name exists in the upload link.

Source: https://docs.pcloud.com/methods/upload_links/uploadtolink.html

# Arguments

  * `code::String`: code of the link

# Optional Arguments

  * `nopartial::Int`: If is set, partially uploaded files will not be saved
  * `progresshash::String`: hash used for observing upload progress

# Output Example

```
{
    result: 0
}
```

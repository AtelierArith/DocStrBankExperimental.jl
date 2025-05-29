```
uploadtransfer(client::PCloudClient; kwargs...)
```

Does a file(s) transfer in way that creates and sends transfer links to receiver emails.

Source: https://docs.pcloud.com/methods/transfer/uploadtransfer.html

# Arguments

  * `sendermail::String`: mail of the sender
  * `receivermails::String`: mail(s) of the receivers(up to 20) separated by ,

# Optional Arguments

  * `message::String`: short message(up to 160 characters) acting as a comment to the receivers
  * `progresshash::String`: hash used for observing transfer progress

# Output Example

```
{
    result: 0
}
```

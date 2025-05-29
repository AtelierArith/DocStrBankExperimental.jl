```
sharerequestinfo(client::PCloudClient; kwargs...)
```

Get information about a share request from the `code` that was sent to the user's email.

Source: https://docs.pcloud.com/methods/sharing/sharerequestinfo.html

# Arguments

  * `code::String`: The code that was sent to the user's email

# Output

Return information about a share.

# Output Example

```
{
    result: 0,
    share: {
        tomail: "pcloud@pcloud.com",
        cancreate: false,
        folderid: 21385,
        sharerequestid: ID,
        canread: true,
        expires: "Thu, 24 Oct 2013 10:41:29 +0000",
        canmodify: false,
        message: "The message",
        candelete: false,
        sharename: "My Share",
        created: "Thu, 03 Oct 2013 10:41:29 +0000"
    }
}
```

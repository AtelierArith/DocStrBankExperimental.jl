```
listshares(client::PCloudClient; kwargs...)
```

List current shares and share requests.

Source: https://docs.pcloud.com/methods/sharing/listshares.html

# Optional Arguments

  * `norequests::Int`: If set, share requests will not be returned
  * `noshares::Int`: If set, established shares will not be returned
  * `noincoming::Int`: If set, hide incoming sub-objects in the result
  * `nooutgoing::Int`: If set, hide outgoing sub-objects in the result

# Output

Returns two objects `shares` and `requests` both with sub-objects `incoming` and `outgoing`.

# Output Example

```
{
    result: 0,
    shares: {
        incoming: [ ],
        outgoing: [ ]
    },
    requests: {
        incoming: [ ],
        outgoing: [
            {
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
        ]
    }
}
```

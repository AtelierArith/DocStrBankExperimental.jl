```
getcollectionpublink(client::PCloudClient; kwargs...)
```

Generates a public link to a collection, owned by the current user.

This method has the same optional parameters as getfilepublink.

*Note:* Public links pointing to a collection have the advantage that are real time image of the collection, while tree links are snapshots.

Source: https://docs.pcloud.com/methods/public_links/getcollectionpublink.html

# Arguments

  * `collectionid::Int`: the id of the collection

# Optional Arguments

  * `expire::datetime`: Datetime when the link will stop working
  * `maxdownloads::Int`: Maximum number of downloads from this folder (even for the same file).
  * `maxtraffic::Int`: Maximum traffic that this link will consume (in bytes, started downloads will not be cut to fit in this limit)
  * `shortlink::Int`: If set, a short link will also be generated

# Output Example

```
{
    "result": 0,
    "link": "https://my.pcloud.com/#page=publink&code=PUBLIC_LINK_CODE",
    "code": "PUBLIC_LINK_CODE",
    "linkid": LINK_ID
}
```

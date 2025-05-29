```
changepublink(client::PCloudClient; kwargs...)
```

Modify a specified public link

Source: https://docs.pcloud.com/methods/public_links/changepublink.html

# Arguments

  * `linkid::Int`: the ID of the link to be changed

# Optional Arguments

One or more of the following optional parameters MUST be specified:

  * `shortlink::Int`: Setting this will create a short link for the link. The response will contain shortcode and shortlink fields.
  * `deleteshortlink::Int`: Setting this will delete the short link associated with the link
  * `expire::datetime`: Sets a new expiration date for the link
  * `deleteexpire::datetime`: If set, deletes link's expiration time (the link will not expire)
  * `maxtraffic::Int`: modifies the traffic limit, set to 0 for unlimited
  * `maxdownloads::Int`: modifies the downloads limit, set to 0 for unlimited

# Output Example

```
{
    result: 0
}
```

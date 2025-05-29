```
getdigest(client::PCloudClient; kwargs...)
```

Returns a digest for digest authentication. Digests are valid for 30 seconds.

Source: https://docs.pcloud.com/methods/general/getdigest.html

# Output

  * `digest::String`: the digest for authentication
  * `expires::datetime`: when the digest expires

# Output Example

```
{
    result: 0,
    digest: "YGtAxbUpI85Zvs7lC7Z62rBwv907TBXhV2L867Hkh",
    expires: "Fri, 27 Sep 2013 10:15:46 +0000"
}
```

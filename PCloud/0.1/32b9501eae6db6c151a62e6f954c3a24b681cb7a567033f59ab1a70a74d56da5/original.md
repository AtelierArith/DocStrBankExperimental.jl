```
acceptshare(client::PCloudClient; kwargs...)
```

Accept a share request.

The request can be either identified by `sharerequestid` as reported by diff or by a `code` that comes from email.

An optional `name` can be specified for the folder name, otherwise the share name will be used.

Implementations are advised to ask for the local name with `name` pre-filled.

Optionally the target folder to mount the share may be identified by `folderid` or `path`.

If the folder is not specified, the user's default folder for accepting shares will be used, if no such folder exists one with suitable name will be created in the user's root directory.

If the optional parameter `always` is set, the accepting user from now on will auto-accept requests from the sharing user to the default share folder.

Source: https://docs.pcloud.com/methods/sharing/acceptshare.html

# Arguments

  * `sharerequestid::Int`: The id of the share request
  * `code::String`: The code that was sent to the user's email

Use `sharerequestid` or `code`.

# Optional Arguments

  * `name::String`: Specify the folder name. Otherwise, use the share name.
  * `folderid::Int`: The id of the folder where to mount the share
  * `path::String`: The filepath to the point where to mount the share
  * `always::Int`: If set, the accepting user from now on will auto-accept requests from the sharing user to the default share folder.

Use `folderid` or `path`.

# Output Example

```
{
    "result": 0
}
```

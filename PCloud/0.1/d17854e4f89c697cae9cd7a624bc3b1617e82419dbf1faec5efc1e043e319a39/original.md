```
createuploadlink(client::PCloudClient; kwargs...)
```

Creates upload link.

Expects `folderid`/`path` of the folder where the uploaded files will be saved. The folder must be owned by the user. Share may be subject to confirmation from the other user.

The folder to be shared is identified by `folderid` or `path`.

Also SHOULD have a `comment` parameter that contains any comments/instructions the user is willing to provide to uploading users. Comments are the only information that uploading users will see (they will not know username of the owner nor the name of the folder they are uploading into) so implementations SHOULD instruct users to fill in at least some description of what is expected from the uploaders (e.g. Hey, that's Mike. Please upload any pictures you took at my wedding here.).

Optional parameter `expire` may indicate a date/time at which the link will stop working.

Also optionally `maxspace` and `maxfiles` may limit maximum total size (in bytes) and total number of files that can be uploaded.

Source: https://docs.pcloud.com/methods/upload_links/createuploadlink.html

# Arguments

  * `folderid::Int`: folder id of the folder, where the uploaded files will be saved
  * `path::String`: path to the shared folder, where the uploaded files will be saved
  * `comment::String`: comment the user is willing to provide to uploading users

Use `path` or `folderid`

# Optional Arguments

  * `expire::datetime`: date/time at which the link will stop working.
  * `maxspace::Int`: limit maximum total size (in bytes)
  * `maxfiles::Int`: otal number of files that can be uploaded

# Output

On success returns

  * `uploadlinkid::Int`: can be used to modify/delete this link
  * `link::String`: full link to a page where files can be uploaded
  * `mail::String`: an email address that also can be used to upload files to this link
  * `code::String`: link's code that can be used to upload files.

{

"result": 0,

"code": "linkCode",

"mail": "somewhere@u.pcloud.com",

"uploadlinkid": linkID,

"link": "https://my.pcloud.com/#page=puplink&code=linkCode"

}

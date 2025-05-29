```
listuploadlinks(client::PCloudClient; kwargs...)
```

Lists all upload links in uploadlinks.

Source: https://docs.pcloud.com/methods/upload_links/listuploadlinks.html

# Output

For each link lists:

  * `uploadlinkid::Int`: can be used to modify/delete this link
  * `link::String`: full link to a page where files can be uploaded
  * `mail::String`: an email address that also can be used to upload files to this link
  * `code::String`: link's code that can be used to upload files
  * `comment::String`: comment of the upload link
  * `files::Int`: number of uploaded files
  * `space::Int`: total space occupied by uploaded files in bytes
  * `metadata::metadata`: target folder's metadata
  * `created::datetime`: when the link was created
  * `last modified::datetime`: when the link was last modified

Optionally if specified at creation time:- `expire::datetime`: date/time at which the link will stop working.

  * `maxspace::Int`: limit maximum total size (in bytes)
  * `maxfiles::Int`: otal number of files that can be uploaded

# Output Example

```
{
    "result": 0,
    "uploadlinks": [
        {
            "space": 23640,
            "files": 23,
            "mail": "somewhere@u.pcloud.com",
            "maxspace": 524288000,
            "created": "Fri, 04 Oct 2013 16:26:41 +0000",
            "code": "linkCode",
            "maxfiles": 100,
            "comment": "Upload link comment",
            "link": "https://my.pcloud.com/#page=puplink&code=linkCode",
            "uploadlinkid": UploadLinkID,
            "modified": "Fri, 04 Oct 2013 16:26:41 +0000",
            "metadata": {
                "isfolder": true,
                "folderid": folderid,
                "thumb": false,
                "icon": "folder",
                "created": "Wed, 18 Sep 2013 10:18:14 +0000",
                "ismine": true,
                "isshared": true,
                "parentfolderid": 0,
                "name": "Simple Upload Place",
                "modified": "Wed, 18 Sep 2013 10:25:57 +0000",
                "id": "id"
            }
        }
    ]
}
```

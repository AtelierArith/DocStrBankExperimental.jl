```
downloadfile(client::PCloudClient; kwargs...)
```

Download a file/s

Downloads one or more files from links suplied in the `url` parameter (links separated by any amount of whitespace) to the folder identified by either `path` or `folderid` (or to the root folder if both are omitted).

The parameter string `progresshash` can be passed. The same should be passed to uploadprogress method.

When monitoring progress with uploadprogress the following fields will be present:

  * `urlcount::Int`: number of URLs requested
  * `urlready::Int`: number of URLs already downloaded
  * `urlworking::Int`: number of currently downloading URLs
  * `finished::Bool`: true if all URLs are downloaded
  * `files::array`: of objects

Each record in `files` has:- `url::String`: the url

  * `status::String`: One of:waiting the link is waiting for its turn to be downloaded

downloading the link is currently being downloaded

ready the file pointed by url is already downloaded

error error occured while downloading (timeout, 404, server not responding)

  * `size::Int`: available only for started downloads only when the server supplied Content-Length - the size of the file
  * `downloaded::Int`: available only for started downloads - number of bytes downloaded so far (goes up to size)
  * `metadata::metadata`: available only for ready downloads - the metadata of the file in the user's filesystem

The files are saved with the names, that are defined from the urls given. These names could be set, using the parameter `target`, which should contain comma-separeted urlencoded list of the desired names. The n-th name in this sequence is given to the n-th url from `url` parameter.

Note that not all urls could have name given with `target`. If so, leave the name empty ( 'name%20A,,name%20C' ), or stop the list on the last desired name (urls can be more than target names).

Source: https://docs.pcloud.com/methods/file/downloadfile.html

# Arguments

  * `url::String`: links separated by any amount of whitespace

# Optional Arguments

  * `path::String`: path to folder, in which to download the files
  * `folderid::String`: folderid of the folder, in which to download the files
  * `target::String`: desired names for the downloaded files

If path or folderid are not present, then root folder is used

# Output

The method returns when all files are downloaded (which might take time). On success `metadata` array with metadata of all downloaded files is returned.

# Output Example

```
{
    "result": 0,
    "metadata": [
        {
            "icon": "image",
            "path": "Simple image.jpg",
            "isshared": false,
            "ismine": true,
            "fileid": 1736716,
            "size": 15604,
            "category": 1,
            "name": "Simple image.jpg",
            "created": "Wed, 02 Oct 2013 15:57:13 +0000",
            "hash": 6306013028049022731,
            "parentfolderid": 0,
            "modified": "Wed, 02 Oct 2013 15:57:28 +0000",
            "thumb": true,
            "isfolder": false,
            "height": 300,
            "width": 222,
            "id": "f1736716",
            "contenttype": "image/jpeg"
        }
    ]
}
```

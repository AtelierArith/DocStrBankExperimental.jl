```
extractarchive(client::PCloudClient; kwargs...)
```

Extracts archive file from the user's filesystem.

Expects as paramters usual `fileid` or `path` of an archive file and `tofolderid` or `topath` for destination folder.

If the archive is password protected, `password` parameter should be provided, otherwise error number 7009 will be returned. Implementations should expect this error code and if encountered prompt user for password and retry the extraction process.

This method runs the extraction process for around 2 seconds. In case it manages to finish in these 2 seconds, `finished` will be set to true in the response. Otherwise `finished` will be `false` and `progresshash` will be provided. This value can be passed to extractarchiveprogress in order to continue the monitoring of the extraction process. In this case also information about current server is returned the same way as provided by currentserver. Monitoring extraction can only be done by sending requests to the same server as returned in the `hostname`.

Unless `nooutput` is set this method also returns `output` array of lines (with no newlines in the end) that are the output of the extraction program. The number returned in `lines` can be used to instruct extractarchiveprogress not to return the same lines of output again.

Source: https://docs.pcloud.com/methods/archiving/extractarchive.html

# Optional Arguments

  * `nooutput::Bool`: if set extraction output is not returned
  * `overwrite::String`: specifies what to do if file to extract already exists in the folder, can be one of 'rename' (default), 'overwrite' and 'skip'
  * `password::String`: password to use to extract a password protected archive

# Output

Described above.

# Output Example

```
{
  "progresshash": "KooPMKmcEBp",
  "ip": "204.155.151.23",
  "hostname": "api5.pcloud.com",
  "ipv6": "::1",
  "result": 0,
  "lines": 10,
  "ipbin": "204.155.151.45",
  "finished": false,
  "output": [
    "Titov.zip: Zip",
    "  Titov/_ART5055.jpg  (1681557 B)... OK.",
    "  Titov/_ART5059.jpg  (1713601 B)... OK.",
    "  Titov/_ART5063.jpg  (1811854 B)... OK.",
    "  Titov/_ART5069.jpg  (1918700 B)... OK.",
    "  Titov/_ART5071.jpg  (1701381 B)... OK.",
    "  Titov/_ART5074.jpg  (1678731 B)... OK.",
    "  Titov/_ART5076.jpg  (1658403 B)... OK.",
    "  Titov/_ART5079.jpg  (1728540 B)... OK.",
    "  Titov/_ART5094.jpg  (1745843 B)... OK."
  ]
}
```

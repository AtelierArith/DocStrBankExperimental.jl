```
preupload_check(datadep, local_filepath[s])::Bool)
```

Peforms preupload checks on the local files without having to download them. This is tool for creating or updating DataDeps, allowing the author to check the files before they are uploaded (or if downloaded directly). This checking includes checking the checksum, and the making sure the `post_fetch_method` runs without errors. It basically performs datadep resolution, but bypasses the step of downloading the files. The results of performing the `post_fetch_method` are not kept. As normal if the DataDep being checked does not have a checksum, or if the checksum does not match, then a warning message will be displayed. Similarly, if the `post_fetch_method` throws an exception, a warning will be displayed.

Returns: true or false, depending on if the checks were all good, or not.

Arguments:

  * `datadep`: Either an instance of a DataDep type, or the name of a registered DataDep as a AbstractString
  * `local_filepath`: a filepath or (recursive) list of filepaths.  This is what would be returned by fetch in normal datadep use.

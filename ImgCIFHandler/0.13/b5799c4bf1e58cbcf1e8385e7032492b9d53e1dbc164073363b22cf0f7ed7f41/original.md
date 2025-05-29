```
create_archives(c::CifContainer; subs = Dict())
```

Create a series of ImageArchive objects, one for each distinct location in `c`. Note that a distinct location is not necessarily a distinct URL, as rsync: and file: URLs may be unique for each frame but correspond to a single directory. `subs` is an optional dictionary keyed by URL, where the value is an existing local directory containing the contents of that URL, uncompressed and with the same directory structure as the archive, so that archive_path can be used to access the image frame.

```
find(path)
find(path, path2,.. ; skip_paths=[])

eachentry(path,..)
findfiles(path,..)  [TODO]
finddupl(path,..)   [TODO]
```

Get file system entries of a directory tree.

  * `find` returns all entries found, including directories and symlinks.
  * `eachentry` does the same, but returns an iterator.
  * `findfiles` only returns regular files and the targets of file symlinks; it also checks if paths are unique (identical paths can, e.g., be caused via symlinks to known files, and are almost never good to have).
  * `finddupl` returns duplicates (a dictionary of <original => [dupes]>); which can be `rm`-ed; only the dupes are deleted.

You can enter multiple paths; useful, e.g., for duplicate-checking a new import directory versus your library.

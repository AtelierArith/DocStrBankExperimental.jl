```
glob(pattern, [directory::AbstractString])
```

Returns a list of all files matching `pattern` in `directory`.

  * If directory is not specified, it defaults to the current working directory.
  * Pattern can be any of:

    1. A `Glob.GlobMatch` object:

        ```
         glob"a/?/c"
        ```
    2. A string, which will be converted into a GlobMatch expression:

        ```
         "a/?/c" # equivalent to 1, above
        ```
    3. A vector of strings and/or objects which implement `occursin`, including `Regex` and `Glob.FilenameMatch` objects

        ```
         ["a", r".", fn"c"] # again, equivalent to 1, above
        ```

          * Each element of the vector will be used to match another level in the file hierarchy
          * no conversion of strings to `Glob.FilenameMatch` objects or directory splitting on `/` will occur.

A trailing `/` (or equivalently, a trailing empty string in the vector) will cause glob to only match directories.

Attempting to use a pattern with a leading `/` or the empty string is an error; use the `directory` argument to specify the absolute path to the directory in such a case.

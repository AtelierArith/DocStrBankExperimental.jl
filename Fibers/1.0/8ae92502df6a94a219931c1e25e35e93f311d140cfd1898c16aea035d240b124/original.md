```
get_tmp_path(tmpdir::String="")
```

Return path to a directory where temporary files can be stored.

Search for candidate directories in the following order:

1. `$``TMPDIR`:  Check if environment variable is defined and directory exists
2. `$``TEMPDIR`: Check if environment variable is defined and directory exists
3. `/scratch`:    Check if directory exists
4. `/tmp`:        Check if directory exists
5. `tmpdir`:      Check if `tmpdir` argument was passed and directory exists

If none of the above exist, use current directory (`./`) and print warning.

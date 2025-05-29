```julia
ishidden(f::AbstractString)
```

Check if a file or directory is hidden.

On Unix-like systems, a file or directory is hidden if it starts with a full stop/period (`U+002e`).  On Windows systems, this function will parse file attributes to determine if the given file or directory is hidden.

!!! note
    Directory references (i.e., `.` or `..`) are always hidden.  To check if the underlying path is hidden, you should run `ishidden` on its `realpath`.


!!! note
    On Unix-like systems, in order to correctly determine if the file begins with a full stop, we must first expand the path to its real path.


!!! note
    On operating systems deriving from BSD (i.e., *BSD, macOS), this function will also check the `st_flags` field from `stat` to check if the `UF_HIDDEN` flag has been set.


!!! note
    On macOS, any file or directory within a [package](https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFBundles/DocumentPackages/DocumentPackages.html) or a [bundle](https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFBundles/AboutBundles/AboutBundles.html) will also be considered hidden.


```
package(prefix::Prefix, output_base::AbstractString,
        version::VersionNumber;
        platform::AbstractPlatform = HostPlatform(),
        verbose::Bool = false, force::Bool = false,
        filter = Returns(true))
```

Build a tarball of the `prefix`, storing the tarball at `output_base`, appending the version number `version`, a platform-dependent suffix and a file extension.  If `platform` is not given, defaults to current platform. Returns the full path to, the SHA256 hash and the git tree SHA1 of the generated tarball.

The are additional keyword arguments:

  * `verbose` controls whether to print information to screen,
  * `force` makes the function overwrite an existing tarball with the same name
  * `filter` is a 2-argument function which returns `true` if the given file or directory should be packaged, and `false` otherwise.  The arguments are `(prefix, path)`, where `prefix` is the directory where the prefix is stored, and `path` is the path, within the prefix, of the file or directory.  This keyword allows you to filter out from the tarball certain files or directories.

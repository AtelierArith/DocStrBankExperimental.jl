```
info_cachefile(pkgname::AbstractString) → cf
info_cachefile(pkgid::Base.PkgId) → cf
info_cachefile(pkgid::Base.PkgId, ji_cachefilename) → cf
```

Return a snapshot `cf` of a package cache file. Displaying `cf` prints a summary of the contents, but the fields of `cf` can be inspected to get further information (see [`PkgCacheInfo`](@ref)).

After calling `info_cachefile("MyPkg")` you can also execute `using MyPkg` to make the image loaded by `info_cachefile` available for use. This can allow you to load `cf`s for multiple packages into the same session for deeper analysis.

!!! warn
    Your session may be corrupted if you run `info_cachefile` for a package that had already been loaded into your session. Restarting with a clean session and using `info_cachefile` before otherwise loading the package is recommended.


```
BBHostPlatform()
```

This provides a stripped-down form of `HostPlatform()` that does not include constraints on the julia version, the libgfortran version, etc... This is useful when you need the most generic form of what will work on the host machine, but don't care about compatibility with all of Julia's deps. This platform will include arch, os, libc type and cxxstring_abi.

DependencyWalker lets you walk through the dependencies of a shared library loaded in Julia.

The package exports a single function, `Library`, which takes as only argument the path to the shared library:

```
julia> using DependencyWalker, LibSSH2_jll

julia> LibSSH2_jll.libssh2_path # Path to the libssh2 library
"/home/user/.julia/artifacts/26c7d3a6c17151277018b133ab0034e93ddc3d1e/lib/libssh2.so"

julia> Library(LibSSH2_jll.libssh2_path)
◼ /home/user/.julia/artifacts/26c7d3a6c17151277018b133ab0034e93ddc3d1e/lib/libssh2.so
  ◼ /usr/bin/../lib/julia/libmbedtls.so.12
    ◼ /usr/bin/../lib/julia/libmbedx509.so.0
...
```

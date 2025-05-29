```
collect_artifact_metas(dependencies::Vector;
                       platform = HostPlatform(),
                       verbose = false)
```

Collect (recursive) JLL dependency artifact metadata for the given `platform`.  Returns a dictionary mapping each (recursive) dependency to its set of artifact metas, which can then be transformed or flattened and given to other tools, such as `symlink_artifact_paths()` or `copy_artifact_paths()`.

Because the dependencies can be specified as a `PkgSpec`, it is possible to request particular versions of a package just as you would with `Pkg.add()`.

The `platform` keyword argument allows for collecting artifacts for a foreign platform, as well as a different Julia version.  This is especially useful for packages that are stdlibs, and thus locked to a single version based on the Julia version.

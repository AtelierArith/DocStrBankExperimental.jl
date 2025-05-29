```
deploy_artifact_paths(dest::AbstractString, artifact_paths;
                      strategy::Symbol = :auto)
```

Deploy the given artifacts into the given destination location, using the specified deployment strategy.  There are three strategies available to use: `:symlink`, `:hardlink` and `:copy`.  By defauly, `deploy_artifact_paths()` will probe to see if `:hardlink` is allowed, and if so use it.  Otherwise, it will fall back to `:copy`, as that is the safest for dealing with executables that expect to be able to use `RPATH` to find dependent libraries at a relative path to themselves.  You can set `:symlink` to force usage of symlinks if you are certain that `:hardlink` will not work, and you do not need the files to reside physically next to eachother.

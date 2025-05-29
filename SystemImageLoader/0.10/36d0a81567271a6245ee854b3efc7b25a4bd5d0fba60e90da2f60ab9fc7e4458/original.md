Defines an interactive artifact installer that the user can run to select the artifacts that they would like to install locally.

```julia
module MySystemImageProvider

using SystemImageLoader

const install = @ArtifactInstaller "../Artifacts.toml"

end
```

Users can then either call `MySystemImageProvider.install()` to get an interactive prompt to select the available images for installation, or run `MySystemImageProvider.install("NameOfImage")` for non-interactive use.

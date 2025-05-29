```
upload_to_gist(
    artifact_id::SHA1,
    [tarball];
    private::Bool = true,
    honor_overrides = false,
    # Following options are aviailable only when `tarball` is not specified:
    name::AbstractString = "$artifact_id.tar.gz",
    extension::AbstractString = ".tar.gz",
) -> gist
```

Create an artifact archive at path `tarball` (or in a temporary location) and upload it to gist. The returned value `gist` can be passed to `add_artifact!`.

# Extended help

## Examples

```julia
using ArtifactUtils
add_artifact!("Artifact.toml", "name", upload_to_gist(artifact_from_directory("source")))
```

creates an artifact from files in the `"source"` directory, upload it to gist, and then add it to `"Artifact.toml"` with the name `"name"`.

## Keyword Arguments

  * `private`: if `true`, upload the archive to a private gist
  * `name`: name of the archive file, including file extension
  * `extension`: file extension of the tarball. It can be used for specifying the compression method.
  * `honor_overrides`: see `Pkg.Artifacts.archive_artifact`

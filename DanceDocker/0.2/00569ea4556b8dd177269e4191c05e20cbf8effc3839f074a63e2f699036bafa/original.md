```
setup(path::String="."; version::String=string(VERSION))
```

  * Julia version number can be overwritten, else defaults to that of system
  * Check if project contains `Project.toml`, `dance.jl` and `settings` dir, else means project is not properly configured with DanceJL
  * Obtain server port (specified under `Dockerfile`) from `Dance.Configuration.Settings` dict
  * Generate `Dockerfile` using template from package `files` dir

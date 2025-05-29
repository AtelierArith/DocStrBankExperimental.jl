```
package_compatible(package_name::String, version::String)
```

Check to see if package_name@version is inbounds with the compat section in your Project.toml

# Arguments

  * `package_name::String`: Name of the package
  * `version::String`: Package version to check being inbounds

# Keywords

  * `toml_path::String`: Path to the Project.toml file

# Returns

  * `Bool`: If the version is in the compat versions

# Throws

  * `PackageNotInCompat`: package_name was not found in the compat section
  * `CompatNotFound`: Compat section not found in the Project.toml
  * `VersionOutsideSpec`: Version is no longer inbounds of the compat versions

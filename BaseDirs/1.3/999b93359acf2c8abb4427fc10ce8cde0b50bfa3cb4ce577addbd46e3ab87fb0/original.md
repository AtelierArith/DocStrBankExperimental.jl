```
 Project
```

A representation of a "Project", namely the essential components of naming information used to produce platform-appropriate project paths.

```
Project(name::Union{AbstractString, Module};
        org::AbstractString="julia", qualifier::AbstractString="lang")
```

The information needed, and the platforms that make use of it, are as follows:

  * `name`, the name of the project (Linux, MacOS, Windows)
  * `org` (`"julia"`), the organisation the project belongs to (MacOS, Windows)
  * `qualifier` (`"org"`), the nature of the organisation, usually a TLD (MacOS)

The resulting "project path components" take one of the following forms:

| Platform |         Project path form |
| --------:| -------------------------:|
|    Linux |            `"$org/$name"` |
|    MacOS | `"$qualifier.$org.$name"` |
|  Windows |            `"$org\$name"` |

**BaseDirs.User**

This module containes accessor functions for user-specific directories.

### Base directory accessors

The functions [`data`](@ref BaseDirs.User.data), [`config`](@ref BaseDirs.User.config), [`state`](@ref BaseDirs.User.state), [`cache`](@ref BaseDirs.User.cache), and [`runtime`](@ref BaseDirs.User.runtime) produce a `String`.

### User directory accessors

The functions [`desktop`](@ref BaseDirs.User.desktop), [`downloads`](@ref BaseDirs.User.downloads), [`music`](@ref BaseDirs.User.music), [`videos`](@ref BaseDirs.User.videos), [`templates`](@ref BaseDirs.User.templates), [`public`](@ref BaseDirs.User.public) produce a `String`.

### Other accessors

The functions [`fonts`](@ref BaseDirs.User.fonts) and [`applications`](@ref BaseDirs.User.applications) produce a `Vector{String}`.

!!! note
    Unlike the [`System`](@ref BaseDirs.System) and "combined" (`BaseDirs.*`) accessors, the *Base* and *User* accessors here return a single directory (`String`).


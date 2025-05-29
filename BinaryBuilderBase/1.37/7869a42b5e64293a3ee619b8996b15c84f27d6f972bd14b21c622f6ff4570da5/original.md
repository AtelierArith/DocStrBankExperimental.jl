An `AbstractDependency` is a binary dependency of the JLL package.  Dependencies are installed to `${prefix}` in the build environment.

Concrete subtypes of `AbstractDependency` are

  * [`Dependency`](@ref): a JLL package that is necessary for to build the package and to load the generated JLL package.
  * [`RuntimeDependency`](@ref): a JLL package that is necessary only at runtime.  Its artifact will not be installed in the prefix during the build.
  * [`BuildDependency`](@ref): a JLL package that is necessary only to build the package.  This will not be a dependency of the generated JLL package.
  * [`HostBuildDependency`](@ref): similar to `BuildDependency`, but it will install the artifact for the host platform, instead of that for the target platform.

Subtypes of `AbstractDependency` should define the following traits:

  * [`is_host_dependency`](@ref)
  * [`is_target_dependency`](@ref)
  * [`is_build_dependency`](@ref)
  * [`is_runtime_dependency`](@ref)
  * [`is_top_level_dependency`][@ref]

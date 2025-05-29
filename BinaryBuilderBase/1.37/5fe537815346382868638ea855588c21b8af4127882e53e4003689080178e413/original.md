An `AbstractSource` is something used as source to build the package.  Sources are installed to `${WORKSPACE}/srcdir` in the build environment.

Concrete subtypes of `AbstractSource` are:

  * [`ArchiveSource`](@ref): a remote archive to download from the Internet;
  * [`FileSource`](@ref): a remote file to download from the Internet;
  * [`GitSource`](@ref): a remote Git repository to clone;
  * [`DirectorySource`](@ref): a local directory to mount.

**BaseDirs**

This module provides utilities to identify the appropriate locations for files.

The [`User`](@ref BaseDirs.User) and [`System`](BaseDirs.System) submodules provide a number of accessor functions, which see.

There are also four combined accessor functions defined, namely: [`data`](@ref BaseDirs.data), [`config`](@ref BaseDirs.config), [`fonts`](@ref BaseDirs.fonts), and [`applications`](@ref BaseDirs.applications). These provide a list of all relevant user and system directories.

As a convenience, the three user-specific accessors [`cache`](@ref BaseDirs.User.cache), [`runtime`](@ref BaseDirs.User.runtime), and [`state`](@ref BaseDirs.User.state), are available under `BaseDirs` as they have no `System` equivalent they could be confused with.

Also see [`BaseDirs.Project`](@ref BaseDirs.Project) for information on how to generate appropriate project paths.

!!! note
    This is essentially an implementation of the XDG (Cross-Desktop Group) directory specifications, with analogues for Windows and MacOS for cross-platform. More specifically, this is a hybrid of:

      * The [*XDG base directory*](https://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html) and the [*XDG user directory*](https://www.freedesktop.org/wiki/Software/xdg-user-dirs/) specifications on Linux
      * The [*Known Folder*](https://msdn.microsoft.com/en-us/library/windows/desktop/dd378457.aspx) API on Windows
      * The [*Standard Directories*](https://developer.apple.com/library/content/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileSystemOverview/FileSystemOverview.html#//apple_ref/doc/uid/TP40010672-CH2-SW6) guidelines on macOS


# Guidelines for appropriate directories

  * **Runtime** data is *volatile*, and only relevant to the current user session. It should be user-specific and non-essential. For example: sockets, named pipes, or lockfiles.
  * **Cache** data is non-essential and can be recreated *without data loss*. For example: thumbnails, compiled bytecode, font paths, or other cached data.
  * **State** data relates to application state, that should persist across *sessions* but doesn't need to be backed up. For example: logs, recently opened files, or other session data.
  * **Config** data is user-specific customisations to application behaviour. For example: theme settings, custom keybindings, media preferences, or other configuration.
  * **Data** content should be used for general application data. For example: saved game progress, library metadata, templates, or other user-specific/user-generated data.
  * **Bin** data is specifically executable files intended to be run by the user.

Essential information (that you'd want to include in backups) should be split across **config** and **data**. Information in **state** may be nice to have, but is non-essential.

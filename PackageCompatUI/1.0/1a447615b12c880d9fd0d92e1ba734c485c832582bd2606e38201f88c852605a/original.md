```
compat_ui()
```

Interactive terminal interface to the `[compat]` section of `Project.toml` for the currently active project.

*Keyword arguments*:

  * `pagesize`: Maximum number of lines used for the UI. Default is 20.
  * `dates`: Whether to show registration date for package versions. Default is true. If disabled the UI starts faster.

*Controls*:

Move up and down with arrow keys. Arrow right and left to enter and leave packages. Use Enter to toggle compatible versions. Quit and save with `q`. Online help with `?`.

When toggling a compatible version, all semantically versioning compatible versions are also set or unset.

*Colors*:

  * Red: No compat information available for the package.
  * Yellow: Compat declared for some versions of the package, but not the latest.
  * Green: Compatible with the latest version of the package.
  * Gray: Package is not registered.

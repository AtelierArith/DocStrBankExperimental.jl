Revise.jl tracks source code changes and incorporates the changes to a running Julia session.

Revise.jl works behind-the-scenes. To track a package, e.g. `Example`:

```julia
(@v1.6) pkg> dev Example        # make a development copy of the package
[...pkg output omitted...]

julia> using Revise             # this must come before the package under development

julia> using Example

[...develop the package...]     # Revise.jl will automatically update package functionality to match code changes

```

Functions in Revise.jl that may come handy in special circumstances:

  * `Revise.track`: track updates to `Base` Julia itself or `Core.Compiler`
  * `includet`: load a file and track future changes. Intended for small, quick works
  * `entr`: call an additional function whenever code updates
  * `revise`: evaluate any changes in `Revise.revision_queue` or every definition in a module
  * `Revise.retry`: perform previously-failed revisions. Useful in cases of order-dependent errors
  * `Revise.errors`: report the errors represented in `Revise.queue_errors`

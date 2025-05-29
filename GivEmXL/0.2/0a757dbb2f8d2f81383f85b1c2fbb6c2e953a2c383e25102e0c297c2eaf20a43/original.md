```
makeproj(tgt_folder, tgt_projname, tgt_scriptname, src::NamedTuple; 
    ignorecase=false, authors::Vector{String}=String[], force=false) → nothing
makeproj(tgt_folder, tgt_projname, tgt_scriptname, src::Symbol; kwargs...)
```

Create a project by copying a template project and performing renamings as necessary. Destination folder must be different from the enclosing folder of the source.

# Arguments

  * `tgt_folder::AbstractString`: Destination folder
  * `tgt_projname::AbstractString`: The name of the project to be created
  * `tgt_scriptname::AbstractString`: The name of the executable script
  * `src::Symbol`: Accepts either `:default` (the default template), or `:example1`    for Toy Example #1, or `:example2` for Toy Example #2 provided with `GivEmXL`
  * `src::@NamedTuple{src_folder::String, src_scriptname::String}`: E.g. it would be    `src=(; src_folder="userproj_template/Template_ProjName", src_scriptname="template_user_scriptname")`    for the default template

# Keyword arguments

  * `ignorecase=false`: Ignore case in the file paths
  * `authors::Vector{T}=String[] where T <: AbstractString`: The project authors (goes to `Project.toml`)
  * `force=false`: If true, will overwrite the destination.

Function `makeproj` is public, not exported.

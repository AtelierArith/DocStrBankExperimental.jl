`opendialog(; value = String[], label = "Open", icon = "far fa-folder-open", options...)`

Creates an [Electron openDialog](https://electronjs.org/docs/api/dialog#dialogshowopendialogbrowserwindow-options-callback). `value` is the list of selected files or folders. `options` (given as keyword arguments) correspond to `options` of the Electron dialog. This widget will not work in the browser but only in an Electron window.

## Examples

```jldoctest
julia> ui = InteractBase.opendialog(; properties = ["showHiddenFiles", "multiSelections"], filters = [(; name = "Text", extensions = ["txt", "md"])]);

julia> ui[]
0-element Array{String,1}
```

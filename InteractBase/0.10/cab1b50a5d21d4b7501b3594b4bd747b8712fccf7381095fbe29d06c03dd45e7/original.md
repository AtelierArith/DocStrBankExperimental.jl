`savedialog(; value = String[], label = "Open", icon = "far fa-folder-open", options...)`

Create an [Electron saveDialog](https://electronjs.org/docs/api/dialog#dialogshowsavedialogbrowserwindow-options-callback). `value` is the list of selected files or folders. `options` (given as keyword arguments) correspond to `options` of the Electron dialog. This widget will not work in the browser but only in an Electron window.

## Examples

```jldoctest
julia> ui = InteractBase.savedialog(; properties = ["showHiddenFiles"], filters = [(; name = "Text", extensions = ["txt", "md"])]);

julia> ui[]
""
```

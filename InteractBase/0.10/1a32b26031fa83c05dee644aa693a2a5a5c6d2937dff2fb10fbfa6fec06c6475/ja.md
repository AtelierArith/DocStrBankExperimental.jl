`opendialog(; value = String[], label = "Open", icon = "far fa-folder-open", options...)`

[Electron openDialog](https://electronjs.org/docs/api/dialog#dialogshowopendialogbrowserwindow-options-callback)を作成します。`value`は選択されたファイルまたはフォルダのリストです。`options`（キーワード引数として与えられる）はElectronダイアログの`options`に対応します。このウィジェットはブラウザでは動作せず、Electronウィンドウ内でのみ動作します。

## 例

```jldoctest
julia> ui = InteractBase.opendialog(; properties = ["showHiddenFiles", "multiSelections"], filters = [(; name = "Text", extensions = ["txt", "md"])]);

julia> ui[]
0-element Array{String,1}
```

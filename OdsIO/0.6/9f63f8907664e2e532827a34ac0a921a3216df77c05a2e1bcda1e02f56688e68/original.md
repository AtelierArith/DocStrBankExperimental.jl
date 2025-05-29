ods_write(filename,data)

Write tabular data (2D Array, DataFrame or Dictionary) to OpenDocument spreadsheet format.

# Arguments

  * `filename`:    an existing ods file or the one to create.
  * `data=Dict()`: a dictionary of locations in the files where to export the data => the actual data (see notes).

# Notes:

  * The locations where to save the data (the keys in the dictionary) are a tuple of tree elements: The first one is the sheet name or sheet position, the other two are the index of row and column of the top left corner where to export the data. If using sheet positions, these must be within current file sheets boundaries. If you want to create new sheets, use names.
  * The actual data exported are either a Matrix (2D Array), a DataFrame or an OrderedDict. In case of DataFrame or OrderedDict the headers ARE exported, so if you don't want them, first convert the DataFrame (or Dictionary) to a Matrix. In case of OrderedDict, the inner data must all have the same length.
  * Some spreadsheet software may not automatically recalculate cells that depends on exported cells (e.g. we are exporting some data o cell `A1` and cells `A2` depends on `A2`, the content of cell `A2` may not be updated after the export). In such case most spreadsheet software have a command to force recalculation of cells (e.g. in LibreOffice/OpenOffice use `CTRL+Shift+F9`)

# Examples

```julia
julia> ods_write("TestSpreadsheet.ods",Dict(("TestSheet",3,2)=>[[1,2,3,4,5] [6,7,8,9,10]]))
```

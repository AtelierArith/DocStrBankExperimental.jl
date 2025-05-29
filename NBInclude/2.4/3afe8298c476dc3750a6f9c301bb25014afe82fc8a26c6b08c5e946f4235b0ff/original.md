```
@nbinclude(path::AbstractString; renumber::Bool=false, counters=1:typemax(Int), regex::Regex=r"", anshook = identity, softscope::Bool = false)
```

Include the IJulia Jupyter notebook at `path` and execute the code cells (in the order that they appear in the file) in `m`, returning the result of the last expression in the last code cell.

Similarly to `include(path)` for `.jl` files, the `path` is relative to the path of the current file (if any), and nested calls to `include` or `nbinclude` are relative to the path of the notebook file.

For code in the `N`-th input cell of the notebook, the `@__FILE__` macro (and other code that uses the file name, e.g. exception backtraces) returns `path:In[N]`, where `N` is the cell number saved in the notebook. If the cell has no number (e.g. if it hasn't been evaluated yet), then it is assigned a number `+N` for the `N`-th nonempty cell.  If `renumber` is set to `true`, then the cell numbers saved in the notebook are ignored and each cell is assigned a consecutive number `N`.

`counters` and `regex` can be used to include only a subset of notebook cells. Only cells for which `counter ∈ counters` holds and the cell text matches `regex` are executed. E.g.

```
@nbinclude("notebook.ipynb"; counters = 1:10, regex=r"# *exec"i)
```

would include cells 1 to 10 from "notebook.ipynb" that contain comments like `# exec` or `# ExecuteMe` in the cell text.

`anshook` can be used to execute a function on all the values returned in the cells.

`softscope` toggles between the "hard" and "soft" scoping rules described in the README.

See also `nbinclude(module, path; ...)` to include a notebook in a specified module.

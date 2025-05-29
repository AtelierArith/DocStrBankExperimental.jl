The NBInclude module allow you to include and execute Julia code from IJulia Jupyter notebooks.  Analogous to `include("myfile.jl")`, just do

```
using NBInclude
@nbinclude("myfile.ipynb")
```

to include the Julia code from the notebook `myfile.ipynb`.  Like `include`, the value of the last evaluated expression is returned.

```
folder(in, [out])
```

Runs all files `*.jl` found in folder `in`, generating a Jupyter `.ipynb` notebook for each, saved in the same folder or in `out` if provided.

Keywords: 

  * `html=true` then converts this notebook to HTML too, using `jupyter nbconvert`.
  * `throw=true` exits with an error if any errors were encountered .
  * `all=true` runs everything, `all=false` will skip any `.jl` files which are older than their `.ipynb` versions.
  * 'verbose=true` adds details about time & computer at the end.
  * `credit=true` adds links.

### `info(GI, showdata::Bool=true; data=true, full=false, crs::Bool=false)`

Shows information about the `GI` grid or image that includes dimensional and, if exists, referencing data.

  * `showdata`: Boolean that controls if a small array subset is printed or not. Alternatively, use `data=false` as a synonym for not showing the data array.
  * `crs`: Boolean that if `true` only prints the referencing information.
  * `full`: For grids print also some more type metadata (var names, etc).

### `info(D::GDtype; crs::Bool=false, attribs=false, att="")`

Shows information about the `D` GMTdataset (or vector of them).

  * `crs`: Boolean that if `true` only prints the referencing information.
  * `attribs`: In case the dataset has attributes, like they do when resulting from reading a shape file, use this parameter to print only the attribute table. A setting of `attribs=true` will print the entire attributes table. Give a positive number, *e.g.* `attribs=5` to show only the first 5 attributes. A negative number prints the last n attribs. A vector range, `attribs=5:9` is also accepted.
  * `att`: Name of one attribute. Returns a string vector with the values of the attribute passed into this option. Example, $attn = info(D, att="NAME")$ returns all values of the attribute $NAME$.

### `info(any)`

Runs $show(stdout, "text/plain", any)$ which prints all elements of `any`. Good for printing the entire vector or matrix.

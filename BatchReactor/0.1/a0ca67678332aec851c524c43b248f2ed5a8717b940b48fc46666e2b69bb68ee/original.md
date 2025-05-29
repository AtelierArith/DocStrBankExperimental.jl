This is the calling function for executing the batch reactor with user defined rate calculation

# Usage

```
batch_reactor(input_file::AbstractString, lib_dir::AbstractString, user_defined::Function; sens= false)
```

  * input_file: the xml input file for batch reactor
  * lib_dir: the direcrtory in which the data files are present. It must be the relative path
  * user_defined : a function that calculates the species source terms. Must be supplied by the user
  * sens : Boolean to be set as true when used along with the sensitivity code

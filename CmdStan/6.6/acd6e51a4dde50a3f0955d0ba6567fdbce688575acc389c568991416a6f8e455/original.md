# stan

Execute a Stan model. 

### Method

```julia
rc, sim, cnames = stan(
  model::Stanmodel, 
  data=Nothing, 
  ProjDir=pwd();
  init=Nothing,
  summary=true, 
  diagnostics=false, 
  CmdStanDir=CMDSTAN_HOME,
  file_run_log=true
)
```

### Required arguments

```julia
* `model::Stanmodel`              : See ?Method
```

### Optional positional arguments

```julia
* `data=Nothing`                  : Observed input data dictionary 
* `ProjDir=pwd()`                 : Project working directory
```

### Keyword arguments

```julia
* `init=Nothing`                  : Initial parameter value dictionary
* `summary=true`                  : Use CmdStan's stansummary to display results
* `diagnostics=false`             : Generate diagnostics file
* `CmdStanDir=CMDSTAN_HOME`       : Location of cmdstan directory
* `file_run_log=true`             : Create run log file (if false, write log to stdout)
* `file_make_log=true`            : Create make log file (if false, write log to stdout)
```

If the type the `data` or `init` arguments are an AbstartcString this is interpreted as a path name to an existing .R file. This file is copied to the coresponding .R data and/or init files for for each chain.

### Return values

```julia
* `rc::Int`                       : Return code from stan(), rc == 0 if all is well
* `samples`                       : Samples
* `cnames`                        : Vector of variable names
```

### Examples

```julia
# no data, use default ProjDir (pwd)
stan(mymodel)
# default ProjDir (pwd)
stan(mymodel, mydata)
# specify ProjDir
stan(mymodel, mydata, "~/myproject/")
# keyword arguments
stan(mymodel, mydata, "~/myproject/", diagnostics=true, summary=false)
# use default ProjDir (pwd), with keyword arguments
stan(mymodel, mydata, diagnostics=true, summary=false)
```

### Related help

```julia
?Stanmodel                         : Create a StanModel
```

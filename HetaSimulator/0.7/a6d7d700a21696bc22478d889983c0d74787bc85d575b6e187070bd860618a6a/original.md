```
load_platform(  
  target_dir::AbstractString;
  rm_out::Bool = true,
  source::String = "index.heta",
  type::String = "heta",
  kwargs...
)
```

Converts heta model to Julia and outputs `Platform` type.

See `heta comiler` docs for details: https://hetalang.github.io/#/heta-compiler/cli-references?id=running-build-with-cli-options

Arguments:

  * `target_dir` : path to a Heta platform directory
  * `rm_out` : should the file with Julia model be removed after the model is loaded. Default is `true`
  * kwargs : other arguments supported by `heta_build`

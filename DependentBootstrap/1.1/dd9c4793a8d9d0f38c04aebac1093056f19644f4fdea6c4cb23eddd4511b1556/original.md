```
BootInput
```

Core type that defines all parameters needed to perform a bootstrap procedure. The vast majority of users should use the keyword argument constructor that has the method signature:

```
BootInput(data ; kwargs...)
```

where data is the dataset to be bootstrapped, and kwargs denotes a set of keyword arguments (defined below) that are used for every exported function in the DependentBootstrap package. The following keyword arguments and default values follow: 

```
- blocklength         <- Block length for bootstrapping procedure. Default value is 0. Set to <= 0 to auto-estimate the optimal block length from the dataset. Float64 inputs allowed.
- numresample         <- Number of times to resample the input dataset. Default value is the module constant NUM_RESAMPLE, currently set to 1000.
- bootmethod          <- Bootstrapping methodology to use. Default value is the Symbol :stationary (for the stationary bootstrap).
- blocklengthmethod   <- Block length selection procedure to use if user wishes to auto-estimate the block length. Default value is the Symbol :ppw2009 (use the method described in Patton, Politis, and White (2009)).
- flevel1             <- A function that converts the input dataset to the estimator that the user wishes to bootstrap. Default value is the sample mean.
- flevel2             <- A function that converts a vector of estimators constructed by flevel1 into a distributional parameter. Default value is sample variance.
- numobsperresample   <- Number of observations to be drawn (with replacement) per resample. The default value is the number of observations in the dataset (the vast majority of users will want this default value).
- fblocklengthcombine <- A function for converting a Vector{Float64} of estimated blocklengths to a single Float64 blocklength estimate. Default value is median.
```

The constructor will attempt to convert all provided keyword arguments to appropriate types, and will notify the user via an error if a supplied keyword argument is not valid.

Note that the bootmethod and blocklengthmethod keyword arguments will accept both Symbol and String inputs, and will convert them to BootMethod and BlockLengthMethod types internally. To see a list of acceptable Symbol or String values for the bootmethod and blocklengthmethod keyword arguments, use: 

```
- collect(keys(DependentBootstrap.BOOT_METHOD_DICT))
- collect(keys(DependentBootstrap.BLOCKLENGTH_METHOD_DICT))
```

respectively. A small proportion of users may need the fine-grained control that comes from constructing BootMethod and BlockLengthMethod types explicitly and then providing them to the keyword constructor. These users should use ?BootMethod and ?BlockLengthMethod at the REPL for more info.

BootInput is not mutable, but the type is near instantaneous to construct, so if a user wishes to amend a BootInput it is recommended to just construct another one. A special constructor is provided to facilitate this process that has the method definition: 

```
- BootInput(data, bootinput::BootInput ; kwargs...)
```

where the new BootInput draws its fields from the keyword arguments that are provided, and then the input BootInput for any keyword arguments that are not provided.

Note that all exported functions in the DependentBootstrap package exhibit the method signature: 

```
- exported_func(data ; kwargs...)
```

which in practice just wraps the keyword argument constructor for a BootInput, and then calls the method signature: 

```
 - exported_func(data, bootinput::BootInput)
```

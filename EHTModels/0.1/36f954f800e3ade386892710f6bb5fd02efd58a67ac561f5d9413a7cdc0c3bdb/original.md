```
AbstractModel
```

The abstract model type. To instantiate your own model type you should subtybe from this model. Additionally you need to implement the following methods to satify the interface: **Mandatory Methods**

  * [`isprimitive`](@ref): defines whether a model is standalone or is defined in terms of other models.  is the model is primitive then this should return `IsPrimitive()` otherwise it returns  `NotPrimitive()`
  * [`visanalytic`](@ref): defines whether the model visibilities can be computed analytically. If yes  then this should return `IsAnalytic()` and the user *must* to define `visibility_point`.  If not analytic then `visanalytic` should return `NotAnalytic()`.
  * [`imanalytic`](@ref): defines whether the model intensities can be computed pointwise. If yes

then this should return `IsAnalytic()` and the user *must* to define `intensity_point`. If not analytic then `imanalytic` should return `NotAnalytic()`.

  * [`radialextent`](@ref): Provides a estimate of the radial extent of the model in the image domain.  This is used for estimating the size of the image, and for plotting.
  * [`flux`](@ref): Returns the total flux of the model.

**Optional Methods:**

  * [`intensity_point`](@ref): Defines how to compute model intensities pointwise. Note this is must be defined if `imanalytic(::Type{YourModel})==IsAnalytic()`.
  * [`visibility_point`](@ref): Defines how to compute model visibilties pointwise. Note this is   must be defined if `visanalytic(::Type{YourModel})==IsAnalytic()`.
  * [`_visibilities`](@ref): Vectorized version of `visibility_point` if you can gain additional speed
  * [`intensitymap`](@ref): Computes the whole image of the model
  * [`intensitymap!`](@ref): Inplace version of `intensitymap`

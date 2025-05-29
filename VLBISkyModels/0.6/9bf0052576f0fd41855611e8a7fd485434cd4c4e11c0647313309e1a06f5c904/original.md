```
ContinuousImage{A<:IntensityMap, P} <: AbstractModel
ContinuousImage(img::Intensitymap, kernel)
```

The basic continuous image model for VLBISkyModels. This expects a IntensityMap style object as its imag as well as a image kernel or pulse that allows you to evaluate the image at any image and visibility location. The image model is

```
I(x,y) = ∑ᵢ Iᵢⱼ κ(x-xᵢ, y-yᵢ)
```

where `Iᵢⱼ` are the flux densities of the image `img` and κ is the intensity function for the `kernel`.

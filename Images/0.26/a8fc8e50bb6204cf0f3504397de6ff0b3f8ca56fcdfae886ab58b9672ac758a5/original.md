Images.jl is an "umbrella package" that exports a set of packages which are useful for common image processing tasks. Most of these packages are hosted at JuliaImages, JuliaArrays, JuliaIO, JuliaGraphics, and JuliaMath.

Images provides an out-of-box toolkit for image processing. This means when you do `using Images`, you load a lot of packages that might require multiple smaller packages, e.g., `using ImageCore, ImageShow, ImageTransformations, FileIO`. However, if you want to reduce package, you should probably use those small packages for a narrower toolbox customized to your specific needs.

The documentation for the JuliaImages ecosystem can be found at https://juliaimages.org. Some dependencies have their own documentation. For instance, the documentation for Colors.jl is hosted in https://juliagraphics.github.io/Colors.jl even though it is included and exported by Images.jl.

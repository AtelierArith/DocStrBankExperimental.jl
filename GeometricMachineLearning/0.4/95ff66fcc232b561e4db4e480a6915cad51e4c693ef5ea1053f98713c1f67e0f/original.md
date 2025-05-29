```
DataLoader(data::AbstractArray{T, 3}, target::AbstractVector)
```

Make an instance of DataLoader for a classification problem. 

Target here is a vector of labels. This is tailored towards being used with the package [`MLDatasets.jl`](https://github.com/JuliaML/MLDatasets.jl).

# Arguments

There are two keyword arguments:

  * `patch_length = 7`. This is the length of the patch in the $x$ and the $y$ direction;
  * `suppress_info = false`.

For the example of the MNIST data set all images are of size $49\times49$. For `patch_length = 7` the image is therefore split into 16 $7\times7$ patches [brantner2023generalizing](@cite).

```
save_logoplot(pfm, background, save_name; dpi=65)
```

# Arguments

  * `pfm::Matrix{Real}`: Position frequency matrix
  * `background::Vector{Real}`: Background probabilities of A, C, G, T
  * `save_name::String`: Name of the path/file to save the plot

Note that

  * `pfm` must be a probability matrix

      * sum of each column must be 1
  * `background` must be a vector of length 4

      * must be a vector of probabilities
      * sum of `background` must be 1

# Example

```julia

pfm =  [0.02  1.0  0.98  0.0   0.0   0.0   0.98  0.0   0.18  1.0
        0.98  0.0  0.02  0.19  0.0   0.96  0.01  0.89  0.03  0.0
        0.0   0.0  0.0   0.77  0.01  0.0   0.0   0.0   0.56  0.0
        0.0   0.0  0.0   0.04  0.99  0.04  0.01  0.11  0.23  0.0]

background = [0.25, 0.25, 0.25, 0.25]

#= save the logo plot in the tmp folder as logo.png =#
save_logoplot(pfm, background, "tmp/logo.png")

#= save the logo plot in the current folder as logo.png with a dpi of 65 =#
save_logoplot(pfm, background, "logo.png"; dpi=65)

```

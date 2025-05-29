```
simulate_pixel(library::SpectralLibrary, max_components::Int64,
                combination_type::String, seed::Int64)
```

Simulate reflectance data for a pixel from a random normalized distribution of endmembers in `library`.

# Arguments

  * `library::SpectralLibrary`: Spectral library containing endmembers and class

information.

  * `max_components::Int64`: Maximum number of endmembers to use in the simulation.
  * `combination_type::String`: The type of combinations to consider when selecting

endmembers (e.g., "all" or "class-even").

  * `seed::Int64`: Seed for the random number generator.

# Returns

  * A tuple containing:

      * `simulated_rfl`: Simulated reflectance spectrum of the pixel.
      * `output_distribution`: A vector of endmember contributions for the pixel.
      * `output_distribution_classes`: A vector of contributions of each unique class.

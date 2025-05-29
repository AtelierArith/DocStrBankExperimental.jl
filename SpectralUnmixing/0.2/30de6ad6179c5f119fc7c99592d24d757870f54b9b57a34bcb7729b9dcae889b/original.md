```
prepare_options(library::SpectralLibrary, combination_type::String,
                 num_endmembers::Vector{Int64}, class_idx)
```

Prepare combinations of endmembers based on the specified combination type.

  * Combination type options:

      * `"class-even"``: Generate all combinations where one endmember is selected from each class.
      * `"all"`: Generate all possible combinations of `num_endmembers` spectra.

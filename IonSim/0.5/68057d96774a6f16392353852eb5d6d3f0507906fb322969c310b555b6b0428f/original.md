```
bgradient!(
        T::Chamber, ion_indxs::Tuple{Int,Int}, transition::Tuple, d::Real
    )
```

Sets the Bfield gradient in place to achieve a detuning `d` between the `transition` of two ions, which are assumed to be of the same species. `ion_indxs` refer to the ordering of the ions in the chain.

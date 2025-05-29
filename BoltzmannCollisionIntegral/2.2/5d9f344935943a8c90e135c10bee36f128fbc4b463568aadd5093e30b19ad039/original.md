```
fload_All(fileLocation,fileName)
```

Loads all the data stored in `fileName` stored at `fileLocation`.

# Example

```julia-repl
    (Parameters,SAtot3,SAtot4,TAtot,SAtal3,SAtal4,TAtal,SMatrix3,SMatrix4,TMatrix1,TMatrix2,p3Max,p4Max,u3MinMax,u4MinMax,SConv3,SConv4,TConv) = fload_All(fileLocation,fileName);
```

Returns a tuple of the data stored in the file. The fields are as follows:

  * `Parameters` : A tuple of the parameters used in the evaluation.
  * `Stot3` : A 6D matrix totalling all the emission spectrum values sampled for 12->34 interaction.
  * `Stot4` : A 6D matrix totalling all the emission spectrum values sampled for 12->43 interaction.
  * `Ttot` : A 4D matrix totalling all the absorption spectrum values sampled.
  * `Stal3` : A 5D matrix of tallies of the number of emission spectrum values sampled for 12->34 interaction.
  * `Stal4` : A 5D matrix of tallies of the number of emission spectrum values sampled for 12->43 interaction.
  * `Ttal` : A 4D matrix of tallies of the number of absorption spectrum values sampled.
  * `SMatrix3` : A 6D matrix of the emission spectrum for 12->34 interaction.
  * `SMatrix4` : A 6D matrix of the emission spectrum for 12->43 interaction.
  * `TMatrix1` : A 4D matrix of the absorption spectrum for 12->34 interaction.
  * `TMatrix2` : A 4D matrix of the absorption spectrum for 21->34 interaction i.e. by permutation of TMatrix1 and correct application of phase space factors if species 1 != species 2.
  * `p3Max` : The maximum value of the momentum space variable p3 sampled for each bin. (Useful for correcting numerical diffusion)
  * `u3MinMax` : The minimum and maximum values of the momentum space variable t3 sampled for each bin. (Useful for correcting numerical diffusion)
  * `p4Max` : The maximum value of the momentum space variable p4 sampled for each bin. (Useful for correcting numerical diffusion)
  * `u4MinMax` : The minimum and maximum values of the momentum space variable t4 sampled for each bin. (Useful for correcting numerical diffusion)
  * `SConv3` : A 6D matrix of the convergence of the emission spectrum compared to the previous run with given `Parameters` for 12->34 interaction.
  * `SConv4` : A 6D matrix of the convergence of the emission spectrum compared to the previous run with given `Parameters` for 12->43 interaction.
  * `TConv` : A 4D matrix of the convergence of the absorption spectrum compared to the previous run with given `Parameters`.

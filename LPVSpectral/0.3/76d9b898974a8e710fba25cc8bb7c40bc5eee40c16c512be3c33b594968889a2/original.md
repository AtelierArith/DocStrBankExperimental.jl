`x,f = ls_spectral(y,t,f=(0:((length(y)-1)/2))/length(y); λ=0)`

perform spectral estimation using the least-squares method `y` is the signal to be analyzed `t` is the sampling points `f` is a vector of frequencies

The difference between `ls_spectral` and `rfft` is `abs.(rfft) = √(2π)abs.(x)`

See also `ls_sparse_spectral` `tls_spectral`

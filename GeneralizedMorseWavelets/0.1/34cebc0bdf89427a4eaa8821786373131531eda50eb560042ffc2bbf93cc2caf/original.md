gmw_grid(β, γ, J, Q; wmin=0,wmax=pi,phase=0.)

Creates a grid of generalized morse wavelets. The grid starts by initiliazing the first wavelet at the lowest scalce with frequency peak `wmax`, it then generates subsequent wavelets by scaling it by a factor `2^(1/JQ)`. `J`is the number of octaves and `Q` the number of inter-octaves. It results in a grid of `JQ` wavelets.

Transfer v to the representation expected by a given context.

For the defalt context, the transfer function does nothing. For other context such as the CUDA version, it may convert integers and floats to other types (e.g. Float32) and Arrays to CuArrays.

You will likely have to implement some transfer operators for your own types if you want to simulate with a non-default context.

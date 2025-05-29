a = margs(mx::Mxpr)

return the arguments `mx`. The arguments `a` are of type `MxprArgType`, which is an alias for `Array{Any,1}`. Many methods for `Mxpr` simply call the same method on `a`. For instance the iterator for `Mxpr` wraps the iterator for `Array{Any,1}`. Thus, iterating over `mx` iterates over the arguments only, not the head.

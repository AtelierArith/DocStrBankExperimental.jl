`get_eps(x::Type)`

Returns the epsilon label for a given `Type`. Defined only for `String` and `Int`, where `<eps>` and `0` are the epsilon symbols. Extend this method if you want to create WFST with a user defined type.

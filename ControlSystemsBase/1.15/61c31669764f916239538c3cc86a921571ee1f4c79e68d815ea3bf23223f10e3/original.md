`bodev(sys::LTISystem, w::AbstractVector; $(Expr(:kw, :unwrap, true)))`

For use with SISO systems where it acts the same as `bode` but with the extra dimensions removed in the returned values.

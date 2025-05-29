```julia
set_title(gp::GnuplotScript,title::AbstractString;
                   enhanced::Bool = false)
```

Define plot title. If `enhanced` is true, some characters are processed in a special way. By example `_` subscripts text.

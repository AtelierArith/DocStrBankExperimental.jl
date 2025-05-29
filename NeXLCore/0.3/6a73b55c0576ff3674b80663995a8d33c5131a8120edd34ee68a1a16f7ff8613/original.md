```
relativeionizationcrosssection(z::Int, ss::Int, ev::AbstractFloat)
relativeionizationcrosssection(ass::AtomicSubShell, ev::AbstractFloat, ::Type{Pouchou1991})
```

An approximate expression based of Pouchou and Pouchoir's 1991 (Green Book) expression for the ionization crosssection plus an additional factor for sub-shell occupancy.

Example:

```
> (/)(map(e->NeXLCore.relativeionizationcrosssection(n"Fe K",e),[10.0e3,20.0e3])...)
0.5982578301818324
```

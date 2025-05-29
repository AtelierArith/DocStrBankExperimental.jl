```
convert_unit(from,to,val)
```

Converts an unit from the unit stored in `from` to the unit stored in `to`. 

When both units are equal, it justs returns `val`. 

If `val` itself is an `unit`, then it converts the from the unit in `val` to the unit in `to`. 

# Examples

```julia-repl
julia> convert_unit(u"Pa",u"kPa",1000.0)      
1.0
```

```julia-repl
julia> convert_unit(u"Pa",u"kPa",1u"atm")     
4053//40
```

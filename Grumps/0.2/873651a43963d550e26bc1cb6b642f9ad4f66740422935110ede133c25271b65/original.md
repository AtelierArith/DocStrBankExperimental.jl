```
DefaultMacroIntegrator( n :: Int, T :: Type; options :: Union{Vec{Symbol}, Nothing} = nothing )
```

Creates a basic Monte Carlo Integrator using n draws.  Type T can be omitted, in which case it is Float64. The optional *options* argument can be used to indicate two possible changes from the default, namely *:randomize* can be used to require randomization and *:replacement* to indicate randomization with  replacement. The default for both is false. Note that *options* is either nothing or a vector of symbols.   A further use of *options* is to specify a column heading containing weight; this symbol should correspond to the desired column heading in the draws spreadsheet. 

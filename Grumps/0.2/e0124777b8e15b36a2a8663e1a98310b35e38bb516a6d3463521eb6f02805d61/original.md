```
DefaultMacroIntegrator( T )
```

Creates a basic Monte Carlo Integrator using 10 000 draws.  This is less than recommended, so use the other method to set a number of your choosing.  Type T can be omitted, in which case it is Float64. The optional *options* argument can be used to indicate two possible changes from the default, namely *:randomize* can be used to require randomization and *:replacement* to indicate randomization with  replacement.  Note that *options* is either nothing or a vector of symbols.  The defaults for both is false. A further use of *options* is to specify a column heading containing weight; this symbol should correspond to the desired column heading in the draws spreadsheet. 

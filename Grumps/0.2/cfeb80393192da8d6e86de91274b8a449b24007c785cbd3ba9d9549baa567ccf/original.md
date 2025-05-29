```
Variables( 
    microspec           :: String,
    macrospec           :: String,
    dummyspec           :: String = "",
    nuisancedummyspec   :: String = "";
    market              :: String = "market",
    product             :: String = "product",
    outsidegood         :: String = "outsidegood",
    marketsize          :: String = "N",
    microinstruments    :: String = "",
    user                :: String = ""
    )
```

This method is used to specify regressors, instruments, random coefficients, interactions, variable labels, etcetera, from the sources you have specified in [`Sources()`](@ref). It creates an object of type *GrumpsVariables*.  There is another method by the same name that accomplishes much the same thing, but has a different user interface. 

The method described here takes string arguments, including two mandatory ones, whereas the other method takes optional arguments only, mostly symbols, vectors of symbols, and matrices of symbols that can be passed in arbitrary order using keywords.  The current method parses user input before calling the other method.

The option *market* specifies the column heading of the column containing the market descriptor (name).  The same is true for all other  arguments, except *outsidegood* which describes the spreadsheet entry that indicates the product is an outside good.  The same label for  the outside good should be used in all spreadsheets and all markets. Outside good entries should only be used in the consumer micro data  and then only if there actually are consumers in the micro data choosing the outside good. All descriptors are case sensitive.

There is a separation between variables that go into the individual consumer utility and ones that only go into "mean utility".  For instance, to specify what goes into individual consumer utility, one could specify

"choice = loginc * msrp + famsize * logfootprint + famsize * van + urban * truck + rc * suv + rc * truck + rc * van"

as the *microspec* argument to indicate that consumer choice is in the micro data set in a column headed "choice" and that there are four interaction terms and three random coefficients.  The interaction terms have the consumer-level variable as the first factor and the product  variable as the second argument.  In this example the three random coefficients are on the suv, truck, and van variables and these variable names should correspond to the column headings in the product level data set.  One can use *constant* to indicate a constant is used: there is no need to include a constant in one's data.

The *macrospec* argument takes the form 

"share = constant + logmpg + loghp + logfootprint + msrp | constant, logmpg, loghp, logfootprint, logcurbweight, lagplcon"

where *share* are product-level market shares, everything between = and | represents regressors, and everything after | represents  instruments; both regressors and instruments are for the product level moments portion.  One can again use *constant* to indicate a constant is used, which need not be included in one's data.

For the remaining arguments, see the description of the other method [`Variables()`](@ref).

```
Variables( ; 
  market              :: Symbol = :market,
  product             :: Symbol = :product,
  choice              :: Symbol = :choice,
  interactions        :: Mat{Symbol} = [],
  randomcoefficients  :: Vec{Symbol} = [],
  outsidegood         :: String = "outsidegood",
  share               :: Symbol = :share,
  marketsize          :: Symbol = :N,
  regressors          :: Vec{Symbol} = [],
  instruments         :: Vec{Symbol} = [],
  dummies             :: Vec{Symbol} = [],
  nuisancedummy       :: Symbol = :none,
  microinstruments    :: Mat{Symbol} = [],
  user                :: Mat{Symbol} = []
    )
```

This method is used to specify regressors, instruments, random coefficients, interactions, variable labels, etcetera, from the sources you have specified in [`Sources()`](@ref). It creates an object of type *GrumpsVariables*.

For instance, the option *market* specifies the column heading of the column containing the market descriptor (name).  The same is true for all other arguments, except *outsidegood* which describes the spreadsheet entry that indicates the product is an outside good.  The  same label for the outside good should be used in all spreadsheets and all markets. Outside good entries  should only be used in the consumer micro data and then only if there actually are consumers in the micro data choosing the outside good. All descriptors are case and space sensitive.

There is a separation between variables that go into the individual consumer utility and ones that only go into "mean utility".  For instance, *interactions* tells Grumps which interaction terms to use and *randomcoefficients* which product level regressors are hit with a random coefficient.  By contrast, *regressors* go into the mean utility component and are regressors in the "second stage" (where β is recovered). One can use the special symbol *:constant* to indicate a constant is to be used; the spreadsheet need not include a column with that heading.

Note that there are three ways that dummy variables can be entered as second stage regressors, which can be useful to incorporate brand, firm, or market effects into δ.  The first is via *regressors*, in which case the onus is on the user to ensure that they have the correct numerical values.  The second possibility is via the *dummies* argument.  For  each symbol passed via the *dummiesi pass one via the *nuisancedummy* argument since it saves both computation time and memory.  There can only be at most one categorical variable that can be converted to nuisance dummies, but there can be arbitrarily many categories.  These dummies and nuisance dummies are automatically assumed to be exogenous and will be included in the instruments, also.

*market* refers to the variable containing the market indicator in all input datasets.  Strings (e.g. "Amarillo, Texas") work best for the market indicators themselves, but it is not a requirement.

*product* refers to the variable containing the product indicator in the product dataset. Strings (e.g. "Camry") work best for the product indicators themselves, but it is not a requirement.

*choice* refers to the variable indicating the choice indicator in the consumer level datasets.  Strings work best for the choice indicators themselves, but it is not a requirement.  These should take the values of the *product* column in the products data set or of the *outsidegood*.

*interactions* refers to the variables indicating consumer and product variable interactions (each row contains consumer variable, product variable)

*randomcoefficients* refers to the product level variables that have a random coefficient on them

*outsidegood* refers to the label used for the outside good

*share* refers to the label used for the product level share; these are shares where the denominator includes the outside good

*marketsize* refers to the size of the market (number of people)

*regressors* refers to the label used for the second stage regressors

*instruments* refers to the label used for the second stage instruments

*dummies* refers to discrete variables to be converted to second stage dummy regressors and instruments

*nuisancedummy* refers to at most one variable to be converted to a second stage dummy regressors and instrument whose coefficient value is of no interest

*microinstruments* refers to micro instruments, which are only relevant for gmm style procedures

*user* refers to a list of variables to be added to the consumer-product interactions using a user-specified procedure.  This is only needed if the Grumps specification itself does not suffice: see [Extending Grumps](@ref) for details.

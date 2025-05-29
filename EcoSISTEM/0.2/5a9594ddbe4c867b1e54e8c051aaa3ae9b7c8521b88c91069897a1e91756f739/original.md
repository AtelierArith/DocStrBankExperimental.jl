worldclimAE(wc::Worldclim_monthly, maxbud::Unitful.Quantity{Float64})

Function to create a `ContinuousTimeHab`, `SimpleBudget` type abiotic environment from a Wordclim type climate.  It either creates a `SimpleBudget` type filled with the maximum budget value `maxbud` or uses a provided budget of type `SolarTimeBudget`.  If a Bool matrix of active grid squares is included, `active`, this is used, otherwise one is all grid cells are considered active.

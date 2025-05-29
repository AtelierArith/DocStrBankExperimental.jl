eraAE(era::ERA, maxbud::Unitful.Quantity{Float64})

Function to create a `ContinuousHab`, `SimpleBudget` type abiotic environment from an ERA type climate. It either creates a `SimpleBudget` type filled with the maximum budget value `maxbud` or uses a provided budget of type `SolarTimeBudget`. If a Bool matrix of active grid squares is included, `active`, this is used, else one is created with all grid cells active.

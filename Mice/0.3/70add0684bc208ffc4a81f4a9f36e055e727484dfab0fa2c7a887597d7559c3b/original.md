```
mice(
    data;
    m::Int = 5,
    imputeWhere::AxisVector{Vector{Bool}} = findMissings(data),
    visitSequence::Vector{String} = makeMonotoneSequence(imputeWhere),
    methods::AxisVector{String} = makeMethods(data),
    predictorMatrix::AxisMatrix{Int} = makePredictorMatrix(data),
    iter::Int = 10,
    progressReports::Bool = true,
    kwargs...
    )
```

Imputes missing values in a dataset using the MICE algorithm.  The output is a `Mids` object.

The data containing missing values (`data`) must be supplied as a `Tables.jl` table.

The number of imputations created is specified by `m`.

`imputeWhere` is an `AxisVector` of boolean vectors specifying where data are to be imputed. The default is to impute all missing data.

The variables will be imputed in the order specified by `visitSequence`.  The default is sorted by proportion of missing data in ascending order;  the order can be customised using a vector of variable names in the desired order. Any column not to be imputed at all can be left out of the visit sequence.

The imputation method for each variable is specified by the `AxisVector` `methods`.  The default is to use predictive mean matching (`pmm`) for all variables. Any variable not to be imputed can be marked as such using an empty string ("").

The predictor matrix is specified by the `AxisMatrix` `predictorMatrix`.  The default is to use all other variables as predictors for each variable.  Any variable not predicting another variable can be marked as such in the matrix using a 0.

The number of iterations is specified by `iter`.

If `progressReports` is `true`, a progress indicator will be displayed in the console.

```
prodIndex(gI,gO,bO,bI;retToScale,prodStructure,convexAssumption,startθ,startμ,startλ)
```

Compute productivity indexes

Given a set of measures of inputs, "good" ("desiderable") and "bad" ("undesiderable") outputs for different decision making units, compute their productivity indexes improvements (or declines) between consecutive time periods.

## Parameters:

  * Positional

      * `gI`: "Good" inputs (3D array by DMUs, input items and periods)
      * `gO`: "Good" outputs (3D array by DMUs, input items and periods)
      * `bO`: "Bad" outputs (3D array by DMUs, input items and periods)
      * `bI`: "Bad" inputs (optional 3D array by DMUs, input items and periods) [default: empty array]
  * Keyword

      * `retToScale`: Wheter the return to scales should be assumed "constant" (default) or "variable"
      * `prodStructure`: Wheter the production structure should be assumed "additive" (default) or "multiplicative"
      * `convexAssumption`: Wheter a convex production frontier should be assumed [default: `true`]

## Returns:

  * A named touple where each element is a matrix of production indexes by DMUs and period passages (e.g. "year2 on year1" and "year3 on year2") or one of their decompositions.
  * Currently the value reported are:

      * `prodIndexes`:          Overall production indexes
      * `prodIndexes_G`:        Decomposition for "good" inputs and outputs
      * `prodIndexes_B`:        Decomposition for "bad" inputs and outputs
      * `prodIndexes_T`:        Decomposition for the technological component, overall
      * `prodIndexes_T_O`:      Decomposition for the technological component, outputs
      * `prodIndexes_T_G_O`:    Decomposition for the technological component, good outputs
      * `prodIndexes_T_B_O`:    Decomposition for the technological component, bad outputs
      * `prodIndexes_T_I`:      Decomposition for the technological component, inputs
      * `prodIndexes_T_G_I`:    Decomposition for the technological component, good inputs
      * `prodIndexes_T_B_I`:    Decomposition for the technological component, bad inputs
      * `prodIndexes_E`:        Decomposition for the efficiency component, overall
      * `prodIndexes_E_O`:      Decomposition for the efficiency component, outputs
      * `prodIndexes_E_G_O`:    Decomposition for the efficiency component, good output
      * `prodIndexes_E_B_O`:    Decomposition for the efficiency component, bad outputs
      * `prodIndexes_E_I`:      Decomposition for the efficiency component, inputs
      * `prodIndexes_E_G_I`:    Decomposition for the efficiency component, good inputs
      * `prodIndexes_E_B_I`:    Decomposition for the efficiency component, bad inputs
      * `prodIndexes_S`:        Decomposition for the scale (residual) component, overall
      * `prodIndexes_S_O`:      Decomposition for the scale (residual) component, outputs
      * `prodIndexes_S_G_O`:    Decomposition for the scale (residual) component, good output
      * `prodIndexes_S_B_O`:    Decomposition for the scale (residual) component, bad outputs
      * `prodIndexes_S_I`:      Decomposition for the scale (residual) component, inputs
      * `prodIndexes_S_G_I`:    Decomposition for the scale (residual) component, good inputs
      * `prodIndexes_S_B_I`:    Decomposition for the scale (residual) component, bad inputs

The second and third element of the tuple are respectively the "good inputs/outputs" and "bad/inputs/outputs" components.

The first matrix can be retrieved from the two components by multiplying them (for `multiplicative` production structure) or summing them (for `additive` production strucure).

## Description of the function

`prodIndex()` displays environmental productivity indices. These productivity measures are implemented for different time periods (eg., years, months etc.) or spatial units (eg., countries, cities etc.), based on the  environmental efficiency indicators described in `efficiencyScores`. Hence, the environmental productivity indices inherit the structure of additive and multiplicative productivity measures.

## Interpretation of the results

The additive productivity indicator shows combined desirable and undesirable outputs productivity improvement (respectively decline) when it takes positive (respectively negative) values.

In the multiplicative context, if the productivity measure is greater (respectively lesser) than 1 then, desirable and undesirable outputs productivity increase (respectively decrease) arises. The BDisposal package underscores the prominent sources of environmental productivity change. The main drivers of productivity variation are technological change, technical efficiency variation and scale efficiency change. For the additive background, when the technological change is greater (respectively, lesser) than 0 then, technological improvement (respectively, deterioration) occurs. A similar reasoning applies for the additive technical and scale efficiency components.

In the multiplicative context, if the technological change is greater (respectively, lesser) than 1 then, technological increase (respectively, decrrease) arises. A similar reasonnng applies for the multiplicative technical and scale efficiency components.

## Example:

```julia
julia> using BDisposal
julia> # 2 DMUs, 2 good Inputs, 2 bad inputs, 3 good outputs and 2 bad outputs. 2 periods
       gI = [1; 3; 5;; 2; 4; 5;;; 1; 4; 5;; 2; 5; 5];
julia> bI = [2; 4; 2;; 3; 7; 5;;; 2; 3; 2;; 3; 6; 5];
julia> gO = [10; 30; 50;; 20; 40; 50;; 15; 8; 12;;; 12; 40; 50;; 22; 50; 50;; 16; 55; 55];
julia> bO = [2; 4; 2;; 3; 7; 5;;; 2; 3; 2;; 3; 6; 5];
julia> analysis = prodIndex(gI,gO,bO,bI,retToScale="variable",convexAssumption=false);
julia> analysis.prodIndexes
3×1 Matrix{Union{Missing, Float64}}:
 1.131370849898476
 3.5322587464470736
 2.140872096444188
```

## Notes:

  * The decomposition by technological, efficiency and scale components is done only for the convex assumption,

as in the non-convex case the individual distance components used to compute these disaggregations are infinite.

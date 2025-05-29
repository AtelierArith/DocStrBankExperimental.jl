```
prodIndexFB(gI,gO,bO,bI;remarcable_obs_dmu,remarcable_obs_period)
```

Compute productivity indexes with a fixed base.

Given a set of measures of inputs, "good" ("desiderable") and "bad" ("undesiderable") outputs for different decision making units, and a specific dmu/time observation to consider as base ("remarcable"), provides the productivity indexes at various time periods.

## Parameters:

  * Positional

      * `gI`: "Good" inputs (3D array by DMUs, input items and periods)
      * `gO`: "Good" outputs (3D array by DMUs, input items and periods)
      * `bO`: "Bad" outputs (3D array by DMUs, input items and periods)
      * `bI`: "Bad" inputs (optional 3D array by DMUs, input items and periods) [default: empty array]
  * Keyword

      * `remarcable_obs_dmu`: Which observation to consider the "remarcable" one [def: `1`]
      * `remarcable_obs_period`: Which tipe period to consider the "remarcable" one [def: `1``]

## Returns:

  * A named touple where each element is a matrix of base-related production indexes by DMUs and time periods.
  * Currently the value reported are:

      * `prodIndexes`:          Overall production indexes

## Description of the function

`prodIndexFB` is a fixed base version of the multiplicative `prodIndex` function. As a result, `prodIndexFB` is based upon the identification of a fixed base observation allowing to compare spatial and/or temporal observations. Specifically, the choice of the base observation for comparisons is affected by the identification of remarkable spatial and/or temporal units.

## Interpretation of the results

`prodIndexFB` > 1 indicates environmentally-adjusted performance improvement. In such case, the remarkable observation produces more good outputs and less bad goods than the compared observation for a given level of good and bad inputs. Alongside, less good and bad inputs are employed by the remarkable observation relatively to the compared observation for given good and bad outputs. If `prodIndexFB < 1`, the reverse reasonning holds.

## Example

```Julia
julia> using BDisposal
julia> # 2 DMUs, 2 good Inputs, 2 bad inputs, 3 good outputs and 2 bad outputs. 2 periods
       gI = [1; 3; 5;; 2; 4; 5;;; 1; 4; 5;; 2; 5; 5];
julia> bI = [2; 4; 2;; 3; 7; 5;;; 2; 3; 2;; 3; 6; 5];
julia> gO = [10; 30; 50;; 20; 40; 50;; 15; 8; 12;;; 12; 40; 50;; 22; 50; 50;; 16; 55; 55];
julia> bO = [2; 4; 2;; 3; 7; 5;;; 2; 3; 2;; 3; 6; 5];
julia> analysis = prodIndexFB(gI,gO,bO,bI;remarcable_obs_dmu=1, remarcable_obs_period=2);
julia> analysis.prodIndexes
3×2 Matrix{Union{Missing, Float64}}:
 0.909091  1.0
 3.63636   2.33766
 1.2987    1.2987
```

## Notes:

  * The function assumes convex, multiplicative production functions with variable returns to scale

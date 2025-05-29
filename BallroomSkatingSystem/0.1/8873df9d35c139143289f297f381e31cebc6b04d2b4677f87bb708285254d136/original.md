```
skating_single_dance(results)
skating_single_dance(results, majority_from; [initial_place, initial_column, depth])
```

Calculates a skating tableau and placement for judgment results of a single dance contained in the DataFrame `results`. It must contain the starter numbers of the dancers as a first column named `:Numbers`, and the places assigned by the different judges in the following columns, for example as in

```julia
DataFrame(Number = [11, 12, 13, 14, 15],
        JudgeA = [1, 2, 3, 4, 5],
        JudgeB = [1, 3, 2, 4, 5],
        JudgeC = [1, 3, 2, 5, 4],
        JudgeD = [5, 1, 2, 3, 4],
        JudgeE = [2, 1, 5, 3, 4])
```

Returns a DataFrame with the skating tableau represented as strings, as well as a DataFrame with the starter numbers and places.

For calculations on cropped tables, the majority of votes, the initial placement to fill, the initial column in the tableau where skating should start as well as the desired depth of the calculation can be defined by keyword arguments.

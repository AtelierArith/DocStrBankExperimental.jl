```
clean_homeaway(dataframe::AbstractDataFrame;invert = missing)
```

Take a dataframe that is formatted with one record for a game between two teams and pivot it such that there exists two records per game, one for each team.

Columns should be formatted such that any columns for data belonging to the home team are prefixed or suffixed with "home**" and "**home", likewise for away teams.

Pass in a list of columns to `invert` to have these values multiplied by -1 before being returned to the new dataframe (such as margin of victory, which may be +7 for a home team and -7 for an away team in a given game).

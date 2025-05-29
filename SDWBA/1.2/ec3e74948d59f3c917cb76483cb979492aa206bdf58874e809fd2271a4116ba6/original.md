Load a scatterer from a file on disk with comma-separated values.

#### Parameters

  * `filename` : String.  Path to the datafile.  This should be a standard .csv file

with columns for the x, y, and z coordinates of the scatterer's centerline, as well as the `a`, `h`, and `g` arguments to Scatterer().

  * `columns` : Optional dictionary of column names. If the columns do not have the names
  * `x`, `y`, `z`, `h`, and `g`, this must be provided.  The keys are the standard column

names and the values are the actual ones in the file.

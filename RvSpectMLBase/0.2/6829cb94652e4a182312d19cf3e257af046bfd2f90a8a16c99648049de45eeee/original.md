Return (chunk*timeseries) that have been trimmed of any chunks that are bad based on any spectra in the chunk*timeseries. For now just checks for NaNs.  Instruments can provide their own checks. Inputs:

  * `chunk_timeseries`: ChunkListTimeseries

Optional arguemnts:

  * `verbose`: print debugging info (false)

Returns:

  * ChunkListTimeseries that has removed problematic chunks.

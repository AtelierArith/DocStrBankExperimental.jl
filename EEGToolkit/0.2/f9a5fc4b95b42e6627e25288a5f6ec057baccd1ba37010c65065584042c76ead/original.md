`nrem(staging::Vector, n::Integer=30, m::Integer=10)`

Finds the `k` underlying NREM periods in a staging vector. Returns a vector of vectors `V` s.t. the `i`th vector in `V`  contains the epochs which comprise the `i`th NREM period. Thus, the length of `V` is `k` the number of NREM periods.

The `n` parameter is the number of (not necessarily consecutive)  epochs which comprise a NREM period. The `m` parameter is the  number of REM or wakefulness epochs required to mark the end  of a NREM period (if `n` NREM epochs were parsed before) or to  disregard the current sequence and begin parsing from the next  NREM epoch.

The `staging` parameter is a vector containing only the  symbols `1, …, 6, ?` where `5` denotes REM, `6` denotes  wakefulness, and `?` denotes unscored/unstaged.

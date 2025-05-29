get_value(d::LoopCategory, n::Int, colname::Symbol)

Return the value corresponding to row `n` of the key datanames for `d` for `colname`.  If `colname` belongs to a child category this will not in general be `colname[n]`. Instead the values of the key datanames are used to look up the correct value 

get*assoc*index(t::TypedDataSource,name,index,other_name)

Return the index of the value in `t[other_name]` corresponding to `name[i]`. If `other_name` has linked key values they will also be checked if `name` is missing. The intended use is for `other_name` to be a linked key data name.

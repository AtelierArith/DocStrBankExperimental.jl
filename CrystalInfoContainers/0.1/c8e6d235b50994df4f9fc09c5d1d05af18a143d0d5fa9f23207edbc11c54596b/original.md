get*key*datanames(d::LoopCategory; drop_same = false)

Return the key datanames for `d` as symbols. If `drop_same` is true, return only those key datanames that could take more than one value, i.e. their parent data names take more than one value.

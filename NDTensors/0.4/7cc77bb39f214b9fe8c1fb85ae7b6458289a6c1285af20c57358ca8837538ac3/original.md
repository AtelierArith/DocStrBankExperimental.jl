BlockSparseTensor(blocks::Vector{Block{N}},                   inds::BlockDims...)

Construct a block sparse tensor with the specified blocks. Defaults to setting structurally non-zero blocks to zero.

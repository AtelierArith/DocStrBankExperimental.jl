blockview(T::DiagBlockSparseTensor, block::Block)

Given a block in the block-offset list, return a Diag Tensor that is a view to the data in that block (to avoid block lookup if the position is known already).

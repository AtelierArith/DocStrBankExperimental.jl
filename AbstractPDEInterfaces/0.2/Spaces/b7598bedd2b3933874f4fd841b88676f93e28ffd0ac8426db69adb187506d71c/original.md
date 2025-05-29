Set transform operator for space acting on vectors like u

args:     - space::AbstractSpace     - u::AbstractVecOrMat input prototype of size (N,) or (N,K)       where N is the length(space). K will be the batch size.

ret:     - space::AbstractSpace with transform operator that can act on `u`

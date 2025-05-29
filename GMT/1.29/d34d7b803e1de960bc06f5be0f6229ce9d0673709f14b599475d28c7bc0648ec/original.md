p = sortslicesperm(A; dims=1, kws...)

Like `sortslices` but return instead the indices `p` such that `A[p, :] == sortslices(A; dims=1, kws...)`

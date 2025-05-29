An `OpSum` represents a sum of operator terms.

Often it is used to create matrix product operator (`MPO`) approximation of the sum of the terms in the `OpSum` oject. Each term is a product of local operators specified by names such as `"Sz"` or `"N"`, times an optional coefficient which can be real or complex.

Which local operator names are available is determined by the function `op` associated with the `TagType` defined by special Index tags, such as `"S=1/2"`, `"S=1"`, `"Fermion"`, and `"Electron"`.

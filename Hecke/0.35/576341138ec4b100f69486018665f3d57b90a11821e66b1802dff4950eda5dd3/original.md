```
diagonal_with_transform(V::AbstractSpace) -> Vector{FieldElem},
                                                         MatElem{FieldElem}
```

Return a vector of elements $a_1,\dotsc,a_n$ such that the space `V` is isometric to the diagonal space $\langle a_1,\dotsc,a_n \rangle$. The second output is a matrix `U` whose rows span an orthogonal basis of `V` for which the Gram matrix is given by the diagonal matrix of the $a_i$'s.

The elements are contained in the fixed field of `V`.

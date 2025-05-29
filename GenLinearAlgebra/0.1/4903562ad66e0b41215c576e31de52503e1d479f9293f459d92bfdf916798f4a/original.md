`transporter(l1, l2 )`

`l1`  and `l2` should be vectors of  the same length of square matrices all of the same size. The result is a basis of the vector space of matrices `A` such  that for any `i` we have  `A*l1[i]=l2[i]*A` –- the basis is returned as  a vector of matrices, empty if the vector space is 0. This is useful to find whether two representations are isomorphic.

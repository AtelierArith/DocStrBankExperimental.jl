gridwise_dot(u::Edges{Primal/Dual},v::Edges{Primal/Dual})

Calculate the dot product of vector grid data `u` and `v`, placing the result on the cell centers (if data are Edges{Primal}) or nodes (if data are Edges{Dual}).

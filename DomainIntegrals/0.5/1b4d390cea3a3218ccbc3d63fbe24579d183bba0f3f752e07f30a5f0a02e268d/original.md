Representation of a weight mapped to a new weight.

Given a weight `w(x)dx` and a map `y=m(x)`, the mapped weight is defined as `w(m(x))/J(m(x))dx`, where `J` is the jacobian determinant of `m`.

The definition is such that we have the following equality after a change of variables:

integral(t->f(t), domain, weight) =     integral(t -> f(inverse(m,t))), m.(domain), MappedWeight(m, weight)

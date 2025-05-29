contains(s::Simplex, pt; atol=0., rtol=defaulrtol(eltype(pt)))

Check if a point is contained inside a Simplex. If the intrinsic dimension of the simplex is smaller then the dimension of the surrounding space (for example a triangle in 3d) one needs the atol, rtol parameters.

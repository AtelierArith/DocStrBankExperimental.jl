Create a CausalLoop (Graph with named vertices) with a vector of vertices, and a vector of pairs of vertices.

CausalLoop([:A, :B], [:A => :B, :B => :B]) will create a CausalLoop with vertices A and B, an edge A => B and an edge B => B.

`face_orientation( m::Mesh{T} )`

Compute a sequence of arrows starting at the barycenter of each face and pointing in the direction of the oriented normal to the face (cross product of 2 first edge vectors).

The size of the arrow is proportional to the sqrt of the area of the triangle formed by the 3 first points of the face.

A Face is typically used when constructing subtypes of `AbstractMesh` where the `Face` should not reproduce the vertices, but rather index into them. Face is parameterized by:

  * `N` - The number of vertices in the face.
  * `T` - The type of the indices in the face, a subtype of Integer.

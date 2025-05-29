```
abstract type AbstractDatabase end
```

Base type to represent databases. A database is a collection of objects that can be accessed like a similar interface to `AbstractVector`. It is separated to allow `SimilaritySearch` methods to know what is a database and what is an object (since most object representations will look as vectors and matrices). 

The basic implementations are:

  * `MatrixDatabase`: A wrapper for object-vectors stored in a `Matrix`, columns are the objects. It is static.
  * `DynamicMatrixDatabase`: A dynamic representation for vectors that allows adding new vectors.
  * `VectorDatabase`: A wrapper for vector-like structures. It can contain any kind of objects.
  * `SubDatabase`: A sample of a given database

In particular, the storage details are not used by `VectorDatabase` and `MatrixDatabase`. For instance, it is possible to use matrices like `Matrix`, `SMatrix` or `StrideArrays`; or even use generated objects with `VectorDatabase` (supporting a vector-like interface).

If the storage backend support it, it is possible to use vector operations, for example:

  * get the `i`-th element `obj = db[i]`, elements in the database are identified by position
  * get the elements list in a list of indices `lst` as `db[lst]` (also using `view`)
  * set a value at the `i`-th element `db[i] = obj`
  * random sampling `rand(db)`, `rand(db, 3)`
  * iterate and collect objects in the database
  * get the number of elements in the database `length(db)`
  * add new objects to the end of the database (not all internal containers will support it)

      * `push_item!(db, u)` adds a single element `u`
      * `append_items!(db, lst)` adds a list of objects to the end of the database

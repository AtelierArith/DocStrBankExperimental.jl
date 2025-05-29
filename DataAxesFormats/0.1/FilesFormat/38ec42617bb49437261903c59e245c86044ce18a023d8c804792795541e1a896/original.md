A `Daf` storage format in disk files. This is an efficient way to persist `Daf` data in a filesystem, and offers a different trade-off compared to storing the data in an HDF5 file.

On the downside, this being a directory, you need to create a `zip` or `tar` or some other form of archive file if you want to publish it. Also, accessing `FilesDaf` will consume multiple file descriptors as opposed to just one for HDF5, and, of course, HDF5 has libraries to support it in most systems.

On the upside, the format of the files is so simple that it is trivial to access them from any programming environment, without requiring a complex library like HDF5. In addition, since each scalar, vector or matrix property is stored in a separate file, deleting data automatically frees the storage (unlike in an HDF5 file, where you must manually repack the file to actually release the storage). Also, you can use standard tools to look at the data (e.g. use `ls` or the Windows file explorer to view the list of properties, how much space each one uses, when it was created, etc.). Most importantly, this allows using standard tools like `make` to create automatic repeatable processing workflows.

We use multiple files to store `Daf` data, under some root directory, as follows:

  * The directory will contain 4 sub-directories: `scalars`, `axes`, `vectors`, and `matrices`, and a file called `daf.json`.
  * The `daf.json` signifies that the directory contains `Daf` data. In this file, there should be a mapping with a `version` key whose value is an array of two integers. The first is the major version number and the second is the minor version number, using [semantic versioning](https://semver.org/). This makes it easy to test whether a directory does/n't contain `Daf` data, and which version of the internal structure it is using. Currently the only defined version is `[1,0]`.
  * The `scalars` directory contains scalar properties, each as in its own `name.json` file, containing a mapping with a `type` key whose value is the data type of the scalar (one of the `StorageScalar` types, with `String` for a string scalar) and a `value` key whose value is the actual scalar value.
  * The `axes` directory contains a `name.txt` file per axis, where each line contains a name of an axis entry.
  * The `vectors` directory contains a directory per axis, containing the vectors. For every vector, a `name.json` file will contain a mapping with an `eltype` key specifying the type of the vector element, and a `format` key specifying how the data is stored on disk, one of `dense` and `sparse`.

    If the `format` is `dense`, then there will be a file containing the vector entries, either `name.txt` for strings (with a value per line), or `name.data` for binary data (which we can memory-map for direct access).

    If the format is `sparse`, then there will also be an `indtype` key specifying the data type of the indices of the non-zero values, and two binary data files, `name.nzind` containing the indices of the non-zero entries, and `name.nzval` containing the values of the non-zero entries (which we can memory-map for direct access). See Julia's `SparseVector` implementation for details.
  * The `matrices` directly contains a directory per rows axis, which contains a directory per columns axis, which contains the matrices. For each matrix, a `name.json` file will contain a mapping with an `eltype` key specifying the type of the matrix element, and a `format` key specifying how the data is stored on disk, one of `dense` and `sparse`.

    If the `format` is `dense`, then there will be a `name.data` binary file in column-major layout (which we can memory-map for direct access).

    If the format is `sparse`, then there will also be an `indtype` key specifying the data type of the indices of the non-zero values, and three binary data files, `name.colptr`, `name.rowval` containing the indices of the non-zero values, and `name.nzval` containing the values of the non-zero entries (which we can memory-map for direct access). See Julia's `SparseMatrixCSC` implementation for details.

Example directory structure:

```
example-daf-dataset-root-directory/
├─ daf.json
├─ scalars/
│  └─ version.json
├─ axes/
│  ├─ cell.txt
│  └─ gene.txt
├─ vectors/
│  ├─ cell/
│  │  ├─ batch.json
│  │  └─ batch.txt
│  └─ gene/
│     ├─ is_marker.json
│     └─ is_marker.data
└─ matrices/
   ├─ cell/
   │  ├─ cell/
   │  └─ gene/
   │     ├─ UMIs.json
   │     ├─ UMIs.colptr
   │     ├─ UMIs.rowval
   │     └─ UMIs.nzval
   └─ gene/
      ├─ cell/
      └─ gene/
```

!!! note
    All binary data is stored as a sequence of elements, in little endian byte order (which is the native order for modern CPUs), without any headers or padding. (Dense) matrices are stored in column-major layout (which matches Julia's native matrix layout).

    All string data is stored in lines, one entry per line, separated by a `


`character (regardless of the OS used).     Therefore, you can't have a line break inside an axis entry name or in a vector property value, at least not     when storing it in`FilesDaf`.

```
When creating an HDF5 file to contain `Daf` data, you should specify
`;fapl=HDF5.FileAccessProperties(;alignment=(1,8))`. This ensures all the memory buffers are properly aligned for
efficient access. Otherwise, memory mapping will be **much** less efficient. A warning is therefore generated
whenever you try to access `Daf` data stored in an HDF5 file which does not enforce proper alignment.
```

That's all there is to it. The format is intentionally simple and transparent to maximize its accessibility by other (standard) tools. Still, it is easiest to create the data using the Julia `Daf` package.

!!! note
    The code here assumes the files data obeys all the above conventions and restrictions. As long as you only create and access `Daf` data in files using [`FilesDaf`](@ref), then the code will work as expected (assuming no bugs). However, if you do this in some other way (e.g., directly using the filesystem and custom tools), and the result is invalid, then the code here may fails with "less than friendly" error messages.


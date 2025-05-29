```
NumPyArrays extends PyCall to provide for additional conversion of Julia
arrays into NumPy arrays without copying.
```

```jldoctest
julia> using NumPyArrays, PyCall

julia> rA = reinterpret(UInt8, zeros(Int8, 4,4));

julia> pytypeof(PyObject(rA))
PyObject <class 'list'>

julia> pytypeof(NumPyArray(rA))
PyObject <class 'numpy.ndarray'>

julia> pytypeof(PyObject(NumPyArray(rA)))
PyObject <class 'numpy.ndarray'>

julia> sA = @view collect(1:16)[5:9];

julia> pytypeof(PyObject(sA))
PyObject <class 'list'>

julia> pytypeof(NumPyArray(sA))
PyObject <class 'numpy.ndarray'>
```

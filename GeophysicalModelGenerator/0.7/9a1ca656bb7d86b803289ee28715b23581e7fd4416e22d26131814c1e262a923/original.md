```
save_LaMEM_markers_parallel(Grid::CartData; PartitioningFile=empty, directory="./markers", verbose=true, is64bit=false)
```

Saves a LaMEM marker file from the `CartData` structure `Grid`. It must have a field called `Phases`, holding phase information (as integers) and optionally a field `Temp` with temperature info. It is possible to provide a LaMEM partitioning file `PartitioningFile`. If not, output is assumed to be for one processor. By default it is assumed that the partitioning file was generated on a 32bit PETSc installation. If `Int64` was used instead, set the flag.

The size of `Grid` should be consistent with what is provided in the LaMEM input file. In practice, the size of the mesh can be retrieved from a LaMEM input file using `read_LaMEM_inputfile`.

# Example

```
julia> Grid    = read_LaMEM_inputfile("LaMEM_input_file.dat")
julia> Phases  = zeros(Int32,size(Grid.X));
julia> Temp    = ones(Float64,size(Grid.X));
julia> Model3D = CartData(Grid, (Phases=Phases,Temp=Temp))
julia> save_LaMEM_markers_parallel(Model3D)
Writing LaMEM marker file -> ./markers/mdb.00000000.dat
```

If you want to create a LaMEM input file for multiple processors:

```
julia> save_LaMEM_markers_parallel(Model3D, PartitioningFile="ProcessorPartitioning_4cpu_1.2.2.bin")
Writing LaMEM marker file -> ./markers/mdb.00000000.dat
Writing LaMEM marker file -> ./markers/mdb.00000001.dat
Writing LaMEM marker file -> ./markers/mdb.00000002.dat
Writing LaMEM marker file -> ./markers/mdb.00000003.dat
```

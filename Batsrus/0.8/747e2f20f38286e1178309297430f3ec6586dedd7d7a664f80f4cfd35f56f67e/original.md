```
 convertTECtoVTU(file::AbstractString, outname="out")
 convertTECtoVTU(head, data, connectivity, outname="out")
```

Convert unstructured Tecplot data to VTK. Note that if using voxel type data in VTK, the connectivity sequence is different from Tecplot: the 3D connectivity sequence in Tecplot is the same as the `hexahedron` type in VTK, but different with the `voxel` type. The 2D connectivity sequence is the same as the `quad` type, but different with the `pixel` type. For example, in 3D the index conversion is:

```
# PLT to VTK voxel index_ = [1 2 4 3 5 6 8 7]
for i in 1:2
	connectivity = swaprows!(connectivity, 4*i-1, 4*i)
end
```

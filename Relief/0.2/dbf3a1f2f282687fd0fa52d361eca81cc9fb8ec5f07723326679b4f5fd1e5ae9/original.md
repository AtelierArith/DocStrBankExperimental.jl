```
vlsrelief(data::Array{<:Real,2}, target::Array{<:Integer,1}, subset_size::Integer=-1, 
               num_subsets::Integer=100; rba::Any=relieff)::Array{Float64,1}
```

Compute feature weights using VLSRelief algorithm. The num*partitions*to*select argument specifies how many partitions to select in each iteration. The num*subsets argument specifies the number of subset iterations to perform. The subset_size argument specifies the size of a partition. The rba argument specifies a (partially applied) wrapped  RBA algorithm that should accept just the data and target values.

---

# Reference:

  * Margaret Eppstein and Paul Haake. Very large scale ReliefF for genome-

wide association analysis. In 2008 IEEE Symposium on Computational Intelligence in Bioinformatics and Computational Biology, CIBCB ’08,

2008. 

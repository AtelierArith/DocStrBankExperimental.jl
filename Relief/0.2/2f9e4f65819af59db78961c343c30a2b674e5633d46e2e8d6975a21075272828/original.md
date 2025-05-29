```
turf(data::Array{<:Real,2}, target::Array{<:Integer,1}, num_it::Integer=50; 
          rba::Any=relieff)::Array{Float64,1}
```

Compute feature weights using TuRF algorithm. The rba argument specifies a (partially applied) wrapped  RBA algorithm that should accept just the data and target values.

---

# Reference:

  * Jason H. Moore and Bill C. White. Tuning ReliefF for genome-wide

genetic analysis. In Elena Marchiori, Jason H. Moore, and Jagath C. Rajapakse, editors, Evolutionary Computation,Machine Learning and Data Mining in Bioinformatics, pages 166–175. Springer, 2007.

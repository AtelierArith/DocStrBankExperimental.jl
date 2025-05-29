```julia
assembleChordsDict(dfg; ...)
assembleChordsDict(dfg, vsyms; MAXADI, lastPoseNum, chords)

```

Calculate the relative chords between consecutive poses in the factor graph. Data structure is Dict{Symbol,Dict{Symbol,Tuple{Matrix,Matrix}}}. The two Matrix values are 3x100, with the first as shown in the attached screen capture. These values should be the relative transform from dict[:x0][:x1], or dict[:x0][:x2], or dict[:x0][:x2] etc for all poses up to some reasonable chord length. There are also two matrix values: the first is the relative transform based on measurements only, the second matrix is the same relative transform but according to the SLAM solution of any and all data being used.

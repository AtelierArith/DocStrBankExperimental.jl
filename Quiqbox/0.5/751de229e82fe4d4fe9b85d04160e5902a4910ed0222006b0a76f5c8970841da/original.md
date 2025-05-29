```
genBFuncsFromText(content::String; 
                  adjustContent::Bool=false, 
                  adjustFunction::Function=sciNotReplace, 
                  excludeFirstNlines::Int=0, excludeLastNlines::Int=0, 
                  center::Union{AbstractArray{T}, 
                                NTuple{D, T}, 
                                NTuple{D, ParamBox{T}}, 
                                SpatialPoint{T, D}, 
                                Missing}=(NaN, NaN, NaN), 
                  unlinkCenter::Bool=false, 
                  normalizeGTO::Union{Bool, Missing}=
                                ifelse(adjustContent, true, missing)) where 
                 {D, T<:AbstractFloat} -> 
Array{<:FloatingGTBasisFuncs, 1}
```

Generate a basis set from `content` which is either a basis set `String` in Gaussian format  or the output from `genBasisFuncText`. For the former, `adjustContent` needs to be set to  `true`. `adjustFunction` is only applied when `adjustContent=true`, which in default is a  `function` used to detect and convert the format of the scientific notation in `content`.

`excludeFirstNlines` and `excludeLastNlines` are used to exclude first or last few lines of  `content` if intended. `center` is used to assign a center coordinate for all the basis  functions from `content`; when it's set to `missing`, it will try to read the center  information in `content`, and leave the center as `[NaN, NaN, Nan]` if one cannot be found  for each corresponding `FloatingGTBasisFuncs`. If `unlinkCenter = true`, the center of each  `FloatingGTBasisFuncs` is a `Base.deepcopy` of the input `center`. Otherwise, they share  the same underlying data so changing the value of one will affect others. If the center  coordinate is included in `content`, it should be right above the subshell information for  the `FloatingGTBasisFuncs`. E.g.:

```
"""
X        1.0                          0.0                          0.0                   
S    1   1.0   false
         2.0                            1.0
"""
```

Finally, `normalizeGTO` specifies the field `.normalizeGTO` of the generated  `FloatingGTBasisFuncs`. If it's set to `missing` (in default), the normalization  configuration of each `FloatingGTBasisFuncs` will depend on `content`, so different basis  functions may have different normalization configurations. However, when it's set to a  `Bool` value, `.normalizeGTO` of all the generated basis functions will be set to that  value.
